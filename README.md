{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "vnet": {
            "type": "string",
            "defaultValue": "[parameters('vnet')]",
            "metadata": {
                "description": "This is vnet parameter"
            }
        },
{
            "subnet1": {
                "type": "string",
                "defaultValue": "[parameters('subnet1')]",
                "metadata": {
                    "description": "description"
                }
            }
        },
        {
            "subnet2": {
            "type": "string",
            "defaultValue": "[parameters('subnet2')]"
            }
        }
    },
    "functions": [],
    "variables": {},
    "resources": [{
        "name": "[parameters('vnet')]",
        "type": "Microsoft.Network/virtualNetworks",
        "apiVersion": "2020-11-01",
        "location": "[resourceGroup().location]",
        "tags": {
            "displayName": "nsr-vnet"
        },
        "properties": {
            "addressSpace": {
                "addressPrefixes": [
                    "10.0.0.0/16"
                ]
            },
            "subnets": [
                {
                    "name": "[parameters('subnet1')]",
                    "properties": {
                        "addressPrefix": "10.0.0.0/24"
                    }
                },
                {
                    "name": "[parameters('subnet2')]",
                    "properties": {
                        "addressPrefix": "10.0.1.0/24"
                    }
                }
            ]
        }
    }],
    "outputs": {}
}
