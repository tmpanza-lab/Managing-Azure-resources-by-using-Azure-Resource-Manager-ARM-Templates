# Managing Azure resources by using Azure Resource Manager (ARM) Templates

## Objective

In this lab, I learnt how to automate resource deployments. I also learnt about Azure Resource Manager templates and Bicep templates and finally about the different ways of deploying the templates.

*Ref 1: Architecture diagram*
 ![image](https://github.com/user-attachments/assets/32463ab8-b181-4e32-9cfb-f8e8704d4aee)


### Job Skills Learned

- Create an Azure Resource Manager template.
- Edit an Azure Resource Manager template and redeploy the template.
- Configure the Cloud Shell and deploy a template with Azure PowerShell.
- Deploy a template with the CLI.
- Deploy a resource by using Azure Bicep.


### Tools Used

- Azure portal - https://portal.azure.com
- Cloud Shell
- Azure PowerShell
- CLI


## Steps

## Task 1: Create an Azure Resource Manager template
In this task, we will create a managed disk in the Azure portal. Managed disks are storage designed to be used with virtual machines. Once the disk is deployed you will export a template that you can use in other deployments.
1.	Sign in to the Azure portal - https://portal.azure.com.
2.	Search for and select Disks.
3.	On the Disks page, select Create.
4.	On the Create a managed disk page, configure the disk and then select Ok.
![image](https://github.com/user-attachments/assets/7dd4da63-99ed-42e2-8a01-3246dbdfbf97)
 
We are creating a simple managed disk so you can practice with templates. Azure managed disks are block-level storage volumes that are managed by Azure.

5.	Click Review + Create then select Create.
6.	Monitor the notifications (upper right) and after the deployment select Go to resource.
![image](https://github.com/user-attachments/assets/cbd91748-6f61-4b2c-9796-c729bd04f9ab)
 
7.	In the Automation blade, select Export template.
8.	Take a minute to review the Template and Parameters files.
![image](https://github.com/user-attachments/assets/8df74b70-8a90-4fde-8d5a-4c4b4aed4ab6)
 
9.	Click Download and save the templates to the local drive. This creates a compressed zipped file.
![image](https://github.com/user-attachments/assets/d6500bc9-5d4a-4e98-9657-65186de9e2d7)
 
10.	Use File Explorer to extract the content of the downloaded file into the Downloads folder on your computer. Notice there are two JSON files (template and parameters).
![image](https://github.com/user-attachments/assets/0bd380a6-3d08-4676-9c9b-5cbac05a5d33)
 


## Task 2: Edit an Azure Resource Manager template and then redeploy the template

In this task, you use the downloaded template to deploy a new managed disk. This task outlines how to quicky and easily repeat deployments.

1.	In the Azure portal, search for and select Deploy a custom template.
2.	On the Custom deployment blade, notice there is the ability to use a Quickstart template. There are many built-in templates as shown in the drop-down menu.
![image](https://github.com/user-attachments/assets/5d9b330c-9ad5-4c22-aa6d-c3d0234e34f0)
 
3.	Instead of using a Quickstart, select Build your own template in the editor.
4.	On the Edit template blade, click Load file and upload the template.json file you downloaded to the local disk.
![image](https://github.com/user-attachments/assets/182e0414-52b1-48d2-a45a-4c4343237071)
 
5.	Within the editor pane, make these changes.
o	Change disks_az104_disk1_name to disk_name (two places to change)
o	Change az104-disk1 to az104-disk2 (one place to change)
![image](https://github.com/user-attachments/assets/1d125820-9f76-4898-a170-d54d6d25aec2)
 
6.	Notice this is a Standard disk. The location is eastus. The disk size is 32GB.
7.	Save your changes.
8.	Don’t forget the parameters file. Select Edit parameters, click Load file and upload the parameters.json.
![image](https://github.com/user-attachments/assets/6d83c886-f286-4893-874e-84641d6be6ed)
 
9.	Make this change so it matches the template file.
Change disks_az104_disk1_name to disk_name (one place to change)
![image](https://github.com/user-attachments/assets/276c1591-3541-4584-b913-e9fdae83fcda)
 
10.	Save your changes.
11.	Complete the custom deployment settings:
![image](https://github.com/user-attachments/assets/9128f4c5-ced7-49c7-8120-2e6720d40f1b)
 
12.	Select Review + Create and then select Create.
![image](https://github.com/user-attachments/assets/fb817908-033c-4397-9d98-490043e07b17)
 
13.	Select Go to resource. Verify az104-disk2 was created.
![image](https://github.com/user-attachments/assets/1cf8b9b6-3d3c-4f6b-a840-b4f844229421)
 
14.	On the Overview blade, select the resource group, az104-rg3. You should now have two disks.
![image](https://github.com/user-attachments/assets/fcebccbc-d622-48e4-8618-fe6ea667ee59)
 
15.	In the Settings section, click Deployments.
![image](https://github.com/user-attachments/assets/7f4a7d00-72cf-4997-96dd-2dd2296c7167)
 
16.	Select a deployment and review the content of the Input and Template blades.
![image](https://github.com/user-attachments/assets/7091ca39-ba3b-4402-949f-c07fc70b20eb)
 
 

## Task 3: Configure the Cloud Shell and deploy a template with PowerShell

In this task, you work with the Azure Cloud Shell and Azure PowerShell. Azure Cloud Shell is an interactive, authenticated, browser-accessible terminal for managing Azure resources. It provides the flexibility of choosing the shell experience that best suits the way you work, either Bash or PowerShell. In this task, you use PowerShell to deploy a template.

1.	Select the Cloud Shell icon in the top right of the Azure Portal. Alternately, you can navigate directly to https://shell.azure.com.
2.	When prompted to select either Bash or PowerShell, select PowerShell.
![image](https://github.com/user-attachments/assets/188a7e96-75f2-45d4-ab2e-978364ca248b)
 
3.	On the Getting started screen select Mount storage account, select your Storage account subscription, and then select Apply.
![image](https://github.com/user-attachments/assets/c8f2b5e3-9360-4698-b002-94de54222435)
 
4.	Select I want to create a storage account and then Next. Complete the Create storage account information.
![image](https://github.com/user-attachments/assets/1eec9c06-2663-42cb-8e37-ca6a29db9145)
![image](https://github.com/user-attachments/assets/758a2779-1684-44fe-850c-df52626437cd)
 
 
5.	When completed select Create.
6.	Select Settings (top bar) and then Go to classic version.
![image](https://github.com/user-attachments/assets/5b3b5c50-d8cc-4a70-bd15-d5993a156f84)
 
7.	Select the Upload/Download files icon (top bar) and then select Upload.
![image](https://github.com/user-attachments/assets/692bc7a5-f186-484c-a50a-08da8b673dff)
 
8.	Upload both the template and parameters files from the Downloads directory.
![image](https://github.com/user-attachments/assets/d4409f96-2fcb-4569-80f2-bdcc05143212)
 
9.	Select the Editor (curly brackets) icon and navigate to the template JSON file on the left in the navigation pane.
![image](https://github.com/user-attachments/assets/c1c32c2b-102d-441d-977d-11080dda201f)
![image](https://github.com/user-attachments/assets/27659190-852d-416b-acdb-18e6f49a609d)
 
 
10.	Make a change. For example, change the disk name to az104-disk3. Use Ctrl +S to save your changes.
![image](https://github.com/user-attachments/assets/50fff859-11ea-4052-b2a0-484be41727ac)
 
11.	To deploy to a resource group, use New-AzResourceGroupDeployment.

New-AzResourceGroupDeployment -ResourceGroupName az104-rg3 -TemplateFile template.json -TemplateParameterFile parameters.json
![image](https://github.com/user-attachments/assets/df8deb07-ee86-4861-bc3d-d37c43613260)
 
12.	Ensure the command completes and the ProvisioningState is Succeeded.
![image](https://github.com/user-attachments/assets/d58b309d-bed8-436f-b5ab-1fffb97d06a8)
 
13.	Confirm the disk was created.
Get-AzDisk
![image](https://github.com/user-attachments/assets/b34e3170-634c-40d8-8271-5915961b46cf)
 

## Task 4: Deploy a template with the CLI
1.	Continue in the Cloud Shell select Bash. Confirm your choice.
![image](https://github.com/user-attachments/assets/4c5f7897-5046-4b9a-bde2-3fa6580f9145)
 
2.	Verify your files are available in the Cloud Shell storage. If you completed the previous task your template files should be available.
![image](https://github.com/user-attachments/assets/68f4c7df-36b9-414b-bf1f-ac4946183d58)
 
3.	Select the Editor (curly brackets) icon and navigate to the template JSON file.
4.	Make a change. For example, change the disk name to az104-disk4. Use Ctrl +S to save your changes.
![image](https://github.com/user-attachments/assets/fec4112b-8540-4549-b931-55846db0e41d)
 
5.	To deploy to a resource group, use az deployment group create.
![image](https://github.com/user-attachments/assets/bd3dbc66-1914-46ef-9c97-908ae91c7809)
 
6.	Ensure the command completes and the ProvisioningState is Succeeded.
![image](https://github.com/user-attachments/assets/ccede964-e65d-4167-9888-6c86eeb3c565)
 
7.	Confirm the disk was created.
  az disk list --output table
![image](https://github.com/user-attachments/assets/03c64b00-04de-4599-81a4-bb7a9804b610)
 

## Task 5: Deploy a resource by using Azure Bicep
In this task, you will use a Bicep file to deploy a managed disk. Bicep is a declarative automation tool that is built on ARM templates.
1.	Continue working in the Cloud Shell in a Bash session.
2.	Locate and download the \Allfiles\Lab03\azuredeploydisk.bicep file.
3.	Upload the bicep file to the Cloud Shell.
![image](https://github.com/user-attachments/assets/b463fe65-cb3b-4606-b6cc-347905b9c998)
 
4.	Select the Editor (curly brackets) icon and navigate to the file.
5.	Take a minute to read through the bicep template file. Notice how the disk resource is defined.
![image](https://github.com/user-attachments/assets/15158649-0410-4f0d-98ef-33a5e1938550)
 
6.	Make the following changes:
o	Change the managedDiskName value to Disk4.
o	Change the sku name value to StandardSSD_LRS.
o	Change the diskSizeinGiB value to 32.
![image](https://github.com/user-attachments/assets/1c02cf92-bab8-4bbd-9574-790712ea2dcc)
 
7.	Use Ctrl +S to save your changes.
8.	Now, deploy the template.
![image](https://github.com/user-attachments/assets/bca004f6-9572-49f8-9957-26148445e652)
 
9.	Confirm the disk was created.
![image](https://github.com/user-attachments/assets/d457381f-dec0-4eea-9b0e-6fea6d423bc5)
 





