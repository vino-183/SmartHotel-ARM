# SmartHotel-ARM

This repository contains an Azure Resource Manager (ARM) template for deploying the **SmartHotel landing zone and application VMs**.  
It provisions:
- SmartHotel Web VMs (smarthotelweb1, smarthotelweb2)
- SmartHotel Ubuntu WAF VM
- SmartHotel SQL VM
- Networking (VNet, subnets, NSGs, Public IPs)
- Application Gateway (SmartHotel-WAF)
- Bastion host (SmartHotelBastion)
- Log Analytics workspace (SmartHotelLA)
- SQL Server + Database

---

## 🚀 Deployment Options

### 1. Azure Portal
1. Log in to [Azure Portal](https://portal.azure.com).
2. Go to **Create a resource** → search for **Template deployment (deploy using custom templates)**.
3. Click **Create**.
4. Upload `azuredeploy.json` from this repo.
5. Fill in parameters (region, admin username, password, resource group).
6. Click **Review + Create** → **Create**.

---

### 2. Azure CLI
Make sure you have the [Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli) installed and logged in.

```bash
az login
az group create --name SmartHotel-RGRG --location "East US"

az deployment group create \
  --resource-group SmartHotel-RGRG \
  --template-file azuredeploy.json \
  --parameters @parameters.json
