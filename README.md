# OpenClaw on Azure (1-click VM deploy)

This repo deploys an Ubuntu VM on Azure **and installs + starts OpenClaw** preconfigured to use an **Azure AI Foundry (ex Azure AI Studio) endpoint that is OpenAI Responses compatible**.

## 1‑click deploy

> You will be prompted for the required variables (SSH key, OpenClaw gateway token, Azure Foundry/OpenAI endpoint + key, model/deployment name, etc.).

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fpookynm%2FOpenClaw_Azure%2Fmain%2Fazuredeploy.json)

## What you get

- Ubuntu 22.04 LTS VM
- Ports opened (restricted to `allowedInboundIp`):
  - `22/tcp` (SSH)
  - `18789/tcp` (OpenClaw Gateway WS)
  - `18790/tcp` (OpenClaw Dashboard/Control UI)

After deployment, check the ARM outputs for:

- `sshCommand`
- `dashboardUrl`
- `gatewayWsUrl`

## Notes

- OpenClaw is installed via the official installer (`https://openclaw.ai/install.sh`).
- The OpenClaw config is written to `~/.openclaw/openclaw.json` on the VM.
- The selected model uses provider `azure-openai-responses/<modelId>` and maps to your deployment name via `AZURE_OPENAI_DEPLOYMENT_NAME_MAP`.
- You must provide the **endpoint base URL** in the deployment parameters (Foundry / Azure OpenAI compatible). Example formats vary by your setup.
