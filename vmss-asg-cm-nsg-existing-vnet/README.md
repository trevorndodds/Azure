<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftrevorndodds%2FAzure%2Fmaster%2Fvmss-asg-cm-nsg-existing-vnet%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https://raw.githubusercontent.com/trevorndodds/Azure/master/vmss-asg-cm-nsg-existing-vnet/azuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>


###### Deploying using existing parameters file (azuredeploy.parameters.json)

1. Modify azuredeploy.parameters.json parameters file accordingly, be aware that this method can expose your local admin credential since it is defined in the parameters file.

2. Open Powershell command prompt, change folder to your template folder.

3. Authenticate to this session

  ```powershell
  Add-AzureRmAccount
  ```

4. Create the new Resource Group where your deployment will happen

  ```powershell
  New-AzureRmResourceGroup -Name "myResourceGroupName" -Location "centralus"
  ```

5. Deploy your template

  ```powershell
  New-AzureRmResourceGroupDeployment -Name "myDeploymentName" `
                                     -ResourceGroupName "myResourceGroupName" `
                                     -Mode Incremental `
                                     -TemplateFile .\azuredeploy.json `
                                     -TemplateParameterFile .\azuredeploy.parameters.json `
                                     -Force -Verbose 
