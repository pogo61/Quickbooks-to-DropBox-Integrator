# Akana API HOOK
![Image of Akana] 
(https://www.akana.com/img/formerlyLOGO8.png) 
[Akana.com](http://akana.com)

## Quickbooks to Dropbox API Integrator
### About the API
- This API retreives the Names and current balances of all the Accounts defined for the QuickBooks Company ID passed to it and stores the list in a JSON object in a text file on Dropbox. The path and name of the file is passed as a JSON object.

### Pre-Reqs
- You must have installed and verified, via the HelloWorld integration, the Dropbox API Hook. 
- You must have installed and verified, via the HelloWorld integration, the Quickbooks API Hook.

### Getting Started Instructions
#### Download and Import
- Download QuickbookstoDropBoxIntegrator.zip
- Download the migrations.properties file, and edit it to replace the <replace this with your key> text with the "Container Key" of the ND or ND cluster in your target PM.
    - the container key is found by going to the "Deatils Tab" of the ND cluster, or ND defined in the Policy Manager Console, then looking at the " Container Overview" tab on that page, and copying the "Container Key:" value. ![container key screenshot](https://github.com/pogo61/Google-Sheets-API-Integration/blob/master/Screen%20Shot%202015-03-18%20at%2011.24.45%20am.png "ND Container Key")
- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the QuickbookstoDropBoxIntegrator.zip archive file 
  - make sure select the migrations.properties file 
  - click Okay to start the importation of the hook.
- this will create a Quickbooks to DropBox Integrator Organisation with the requisite artefacts needed to run the API.

#### Verify Import
- Expand the services folder in the Quickbooks to DropBox Integrator you imported and find Quickbooks_to_DropBox_Integrator VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Quickbooks to DropBox Integrator Organisation you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- Nil.

#### Verify Connectivity
- Using ```curl -X POST -d '{"filename":"quickbooks/Account Details.txt"}' http://ec2-107-21-253-123.compute-1.amazonaws.com:9905/quickbooks_int/export?company_id=1353176045 --header "Content-Type:application/json" --header "QBAuthKey:dnr3h34fkw" --header "DBAuthKey:a9gnwbivaa8"```
-  the response should be similar to the below, assuming all the parameters are correctt:  
```{"Result": "Success"}```
  

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license

