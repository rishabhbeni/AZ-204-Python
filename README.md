Links to all Azure Development Python Labs
-------------------------------------------

1.) Azure App Service:

Deploy a Python (Django or Flask) web app to Azure App Service - https://learn.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=flask%2Cwindows%2Cazure-cli%2Cvscode-deploy%2Cdeploy-instructions-azportal%2Cterminal-bash%2Cdeploy-instructions-zip-azcli

2.) Azure Functions:

Create a function in Azure with Python using Visual Studio Code - https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-python?pivots=python-mode-configuration
Create your first durable function in Python - https://learn.microsoft.com/en-us/azure/azure-functions/durable/quickstart-python-vscode?tabs=windows

3.) Azure Blob Storage:

Azure Blob Storage client library for Python - https://learn.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-python?tabs=managed-identity%2Croles-azure-portal%2Csign-in-azure-cli

4.) Azure Cosmos DB:

Azure Cosmos DB for NoSQL client library for Python - https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/quickstart-python?tabs=azure-portal%2Cpasswordless%2Cwindows%2Csign-in-azure-cli%2Csync

5.) Infrastructure as a Service:

Create a Linux virtual machine with the Azure CLI - https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-cli
Create ARM templates with Visual Studio Code - https://learn.microsoft.com/bs-latn-ba/azure/azure-resource-manager/templates/quickstart-create-templates-use-visual-studio-code?tabs=CLI
Create a private container registry using the Azure CLI - https://learn.microsoft.com/en-us/azure/container-registry/container-registry-get-started-azure-cli
Deploy a container instance in Azure using the Azure CLI - https://learn.microsoft.com/en-us/azure/container-instances/container-instances-quickstart

6.) Authentication and Authorization:

Add sign-in with Microsoft to a web app - https://learn.microsoft.com/en-us/azure/active-directory/develop/web-app-quickstart?pivots=devlang-python

7.) Secure Cloud Solutions:

Use Azure Key Vault with a virtual machine in Python - https://learn.microsoft.com/en-us/azure/key-vault/general/tutorial-python-virtual-machine?tabs=azure-cli
Create a Python app with Azure App Configuration - https://learn.microsoft.com/en-us/azure/azure-app-configuration/quickstart-python-provider?tabs=windowscommandprompt

8.) API Management:

Create a new Azure API Management service instance by using the Azure CLI - https://learn.microsoft.com/en-us/azure/api-management/get-started-create-service-instance-cli

9.) Event Based Solutions:

Route storage events to web endpoint with Azure CLI - https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-event-quickstart?toc=%2Fazure%2Fevent-grid%2Ftoc.json
Send events to or receive events from event hubs by using Python - https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-python-get-started-send?tabs=passwordless%2Croles-azure-portal

10.) Message Based Solutions:

Send messages to and receive messages from Azure Service Bus queues- https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-python-how-to-use-queues?tabs=passwordless
Azure Queue Storage client library for Python - https://learn.microsoft.com/en-us/azure/storage/queues/storage-quickstart-queues-python?tabs=passwordless%2Croles-azure-portal%2Cenvironment-variable-windows%2Csign-in-azure-cli

11.) Monitoring & Logging:

Set up Azure Monitor for your Python application - https://learn.microsoft.com/en-us/azure/azure-monitor/app/opencensus-python

12.) Caching & Content Delivery Solutions:

Use Azure Cache for Redis in Python - https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/cache-python-get-started
Create an Azure CDN profile and endpoint - https://learn.microsoft.com/en-us/azure/cdn/cdn-create-new-endpoint?toc=%2Fazure%2Ffrontdoor%2FTOC.json


Case Study on Azure Development
--------------------------------

Task 1 - Publish the Full Stack Python Application on Azure

Step 1: Go to Visual Studio Code. Open the folder containing your web application
Step 2: Launch Terminal from View menu and run az login command
Step 3: Then run the command az webapp up --runtime PYTHON:3.8 --sku B1 --logs
Step 4: This will create a new resource group, App Service Plan and a web app for you. If you want to use an existing resource use the name of your existing App and Plan in the command
Step 5: Once it is published nvaigate to your web app in Azure Portal by browsing your app URL

Reference - https://learn.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=flask%2Cwindows%2Cazure-cli%2Cvscode-deploy%2Cdeploy-instructions-azportal%2Cterminal-bash%2Cdeploy-instructions-zip-azcli


Task 2 - Use Deployment Slots to swap the test and production environment

Step 1: Go to the web app in Azure and from the left blade click on scale up. Choose Standard (S1) plan and apply it
Step 2: Go to your App Service in Azure and create new Deployment Slot named test
Step 3: Install the App Service extension in Visual Studio
Step 4: Configure auto-swapping for test and production slot from the terminal by running the following command az webapp deployment slot auto-swap --name <web-app-name> --resource-group <resrource-group-name> --slot test
Step 5: Make changes to index.html or any other page of your app and save it
Step 6: Go to Azure extension from Visual Studio sidebar and select your your app service from the list of subscriptions and services
Step 7: Expand the web app and select your Deployment slot (test)
Step 8: Right click on it and select deploy to slot
Step 9: Then select deploy and wait for your deployment to be completed
Step 10: Go Route 50% of the traffic to the production slot and rest 50% to the test slot

Reference - 

1. https://learn.microsoft.com/en-us/azure/app-service/manage-scale-up
2. https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots
3. https://learn.microsoft.com/en-us/cli/azure/webapp/deployment/slot?view=azure-cli-latest#az-webapp-deployment-slot-auto-swap


Task 3 - Enable Autoscaling rules for the web app

Step 1: Go to your App Service (Production Slot) and select scale out
Step 2: Click on Custom AutoScale and change the name of your rule to match the desired syntax
Step 3: Set the minimum, maximum and default value to 1,3 & 1 respectively
Step 4: Then Select based on metrics and click on add a rule
Step 5: Select CPU percentage as the metric name
Step 6: For Operator use Greater than or equal to and for Metric threshold to trigger scale action type 20
Step 7: Change the duration to 5 minutes and click on add
Step 8: Add a similar rule with Operator only Less than and changing duration to again 5 minutes
Step 9: Save the rule and wait for 5 minutes for it to take effect
Step 10: Trigger notification on your email and save it

Reference - https://learn.microsoft.com/en-us/azure/azure-monitor/autoscale/autoscale-get-started?toc=%2Fazure%2Fapp-service%2Ftoc.json


Task 4 - Enable Authentication for the web app

Step 1: Go to Authentication Tab and click on Identity Proiver
Step 2: Select Microsoft. Leave rest of the values default and click on Add
Step 3: Go to Active Directory and then users. Invite or add a new user as a guest user with a different ID registered to Azure AD
Step 4: Go to your web app and click on Browse
Step 5: Sign in with the secondary ID or let the other user sign in to confirm your app is accessible only from your Azure AD tenant

Reference - https://learn.microsoft.com/en-us/azure/app-service/scenario-secure-app-authentication-app-service


Task 5 - Configure APIs using API Management

Step 1: Go to API management section from your app service and create a new APIM service using Developer tier
Step 2: Link your APIs from App Service to API Management service
Step 3: Enable System Assigned Managed Identity for your web app and save it
Step 4: Once enabled, click on add role assignments and select scope as Resource Group
Step 5: Select your Resource Group and search for API in roles
Step 6: Add API Management Service Reader/Contributor role for GET/POST queries and save it
Step 7: Go to your APIM instance and select the API from your web app
Step 8: Go to policies in Design tab and add an Inbound policy
Step 9: Select Rate-Limit-By-Key and limit the requests to 3 in 60 seconds
Step 10: Save the policy and go to test tab. Then select GET operation and hit send 3 times to test the API calls

Reference -

1. https://learn.microsoft.com/en-us/azure/api-management/get-started-create-service-instance
2. https://learn.microsoft.com/en-us/azure/api-management/rate-limit-by-key-policy
3. https://learn.microsoft.com/en-us/azure/app-service/overview-managed-identity?context=%2Fazure%2Factive-directory%2Fmanaged-identities-azure-resources%2Fcontext%2Fmsi-context&tabs=portal%2Chttp


Task 6 - Route Events to Storage Queue using Event Grid

Step 1: Create a Storage Account with a unique name and LRS redundancy
Step 2: Go to Events section in App Service Blade
Step 3: Click on add an Event Subscription and enter name for it
Step 4: In System Topic Name enter a name to create Event Grid Topic
Step 5: Select Storage Queues as the Endpoint Type and click on Select an endpoint
Step 6: Select the Subscription and the Storage Account created earlier
Step 7: Create a new queue and enter the name. Then click Select
Step 8: Go to your Topic and enable System Assigned Managed Identity with Storage Account Data Contributor role for your Storage Account. Then come back to creating your Event Grid Subscription and enter the basic details again
Step 9: Select System Assigned for Managed Identity type
Step 10: Click on Create and check the queue for messages after swapping the slots again

Reference - 

1. https://learn.microsoft.com/en-us/azure/storage/queues/storage-quickstart-queues-portal
2. https://learn.microsoft.com/en-us/azure/event-grid/compare-messaging-services
3. https://learn.microsoft.com/en-us/azure/event-grid/custom-event-to-queue-storage


Task 7 - Cache the app using CDN Endpoints

Step 1: In your App Service blade, go to Networking and click on Azure CDN
Step 2: In CDN Profile, click on Create new and enter the name and choose Microsoft Standard for pricing details of the profile
Step 3: Then enter the CDN endpoint name and click on Create
Step 4: Once endpoint has been added, after 10 minutes navigate to it and browse the endpoint hostname
Step 5: After making changes to the frontend of your app, deploy your app again and access through the CDN endpoint to test

Reference - https://learn.microsoft.com/en-us/azure/cdn/cdn-add-to-web-app?toc=%2Fazure%2Ffrontdoor%2FTOC.json


Task 8 - Monitor App Performance using Application Insights

Step 1: Go to your Web App and turn on Application Insights by creating a new resource
Step 2: Then go to your APIM and click on Application Insights under Monitoring section. Add your existing App Insights resource and click on Create
Step 3: Now go the App Insights resource and click on Availability Tests. Add a Classic test and enter the name for the test
Step 4: Add the URL for your web app and with rest of the parameters as default, click on Create
Step 5: Go to Application Map and check with the performance of your app after 5 minutes of adding the test

Reference - https://learn.microsoft.com/en-us/azure/azure-monitor/app/monitor-web-app-availability
