### Appning Utilities

## This project contains the following util functions required by SVM React app
1. Handling API calls

## Pre-requisites:
**code.solverminds.net** repository must be configured in your machine to serve as npm repository. Follow the below steps to configure npm repository.

**Step1:**
Create .npmrc file in your machine in the following path.

Ubuntu: /home/```<accountname>```/.npmrc

Windows: C:/users/```<accountname>```/.npmrc

**Step2:**
Add the following content to the created .npmrc file.

registry=http://code.solverminds.net:8081/repository/npm-group/

_auth=YWRtaW46YWRtaW4xMjM=

Note: This is one time setup.

## How to integrate?

**Step 1:** Install appning-util module

Ubuntu: sudo npm install --save appning-util

Windows: npm install --save appning-util

**Step 2:** Update the following line under scripts section in package.json. This is to configure global webservice / API base URL. This base URL is applicable only in development mode of node.

Existing :
                
                "scripts": {
                     "start": "react-scripts start",

New:
Ubuntu

                "scripts": {
                     "start": "REACT_APP_API_URL=http://localhost:8080 react-scripts start"

Windows

                "scripts": {
                     "start": "SET \"REACT_APP_API_URL=http://localhost:8080\" && react-scripts start",

Base URL can be repalced with API or REST service IP and port.


Step 3: Add the following line in App.js under   ```<MuiPickersUtilsProvider utils={MomentUtils}>```. This is to handle and display error messages like 404 - Page not found or any other connection related errors.

```<AppningUtil />```

Example:

App.js

                import {AppningUtil} from 'appning-util/commons';
                ....
                 <MuiPickersUtilsProvider utils={MomentUtils}>
                 <AppningUtil />
                .....

How to use smfetch?

This is working based on Axios API. We can use **smfetch()** instead of **axios**.

                import {smfetch} from 'appning-util/commons';

                ...
                //Get request
                smfetch().get('usermanagement/users')
                .then(function (response) {
                     //logic
                 }).catch(function (error) {
                  //logic
                })

                //POST request
                smfetch().post('usermanagement/users',{data})
                .then(function (response) {
                //logic

                }).catch(function (error) {
                //logic
                })

All other request types(PUT, DELETE, etc.,) follows the same pattern.

How to use dialogUtil?

instead of implementing **dilog Component** we can use **DialogUtil** package from appning-util library

                import {dialogUtil} from 'appning-util/commons';

                ...
                //for information message
                dialogUtil.info(header,message);
                              
                //for error message
                  dialogUtil.error(header,message);

                //for warning message
                  dialogUtil.warning(header,message);

                //for success message
                  dialogUtil.success(header,message);

                //for confirm Dialog
                  dialogUtil.confirm(header,message,onConfirm(),onReject(),yeslabel,nolabel);
               
               //example for passing parameter in function
               dialogUtil.confirm("Dataset","Sure You Want to Delete Table ",()=>removeTable(tableid),null,"delete","No")
               
