---
title: Connect an existing Azure Cosmos account with virtual network service endpoints
description: Connect an existing Azure Cosmos account with virtual network service endpoints
author: markjbrown
ms.author: mjbrown
ms.service: cosmos-db
ms.subservice: cosmosdb-sql
ms.topic: sample
ms.date: 9/25/2019
---

# Connect an existing Azure Cosmos account with virtual network service endpoints using Azure CLI

[!INCLUDE [cloud-shell-try-it.md](../../../../../includes/cloud-shell-try-it.md)]

If you choose to install and use the CLI locally, this topic requires that you are running the Azure CLI version 2.0.73 or later. Run `az --version` to find the version. If you need to install or upgrade, see [Install Azure CLI](/cli/azure/install-azure-cli).

## Sample script

This sample is intended to show how to connect an existing Azure Cosmos account to an existing new virtual network where the subnet is not yet configured for service endpoints by using the `ignore-missing-vnet-service-endpoint` parameter. This allows the configuration for the Cosmos account to complete without error before the configuration to the virtual network's subnet is completed. Once the subnet configuration is complete, the Cosmos account will then be accessible through the configured subnet.

> [!NOTE]
> This sample demonstrates using a SQL (Core) API account. To use this sample for other APIs, apply the `enable-virtual-network` and `virtual-network-rules` parameters in the script below to your API specific script.

[!code-azurecli-interactive[main](../../../../../cli_scripts/cosmosdb/common/service-endpoints-ignore-missing-vnet.sh "Create an Azure Cosmos account with service endpoints.")]

## Clean up deployment

After the script sample has been run, the following command can be used to remove the resource group and all resources associated with it.

```azurecli-interactive
az group delete --name $resourceGroupName
```

## Script explanation

This script uses the following commands. Each command in the table links to command specific documentation.

| Command | Notes |
|---|---|
| [az group create](/cli/azure/group#az-group-create) | Creates a resource group in which all resources are stored. |
| [az network vnet create](/cli/azure/network/vnet#az-network-vnet-create) | Creates an Azure virtual network. |
| [az network vnet subnet create](/cli/azure/network/vnet/subnet#az-network-vnet-subnet-create) | Creates a subnet for an Azure virtual network. |
| [az network vnet subnet show](/cli/azure/network/vnet/subnet#az-network-vnet-subnet-show) | Returns a subnet for an Azure virtual network. |
| [az cosmosdb create](/cli/azure/cosmosdb#az-cosmosdb-create) | Creates an Azure Cosmos DB account. |
| [az network vnet subnet update](/cli/azure/network/vnet/subnet#az-network-vnet-subnet-update) | Updates a subnet for an Azure virtual network. |
| [az group delete](/cli/azure/resource#az-resource-delete) | Deletes a resource group including all nested resources. |

## Next steps

For more information on the Azure Cosmos DB CLI, see [Azure Cosmos DB CLI documentation](/cli/azure/cosmosdb).

All Azure Cosmos DB CLI script samples can be found in the [Azure Cosmos DB CLI GitHub Repository](https://github.com/Azure-Samples/azure-cli-samples/tree/master/cosmosdb).
