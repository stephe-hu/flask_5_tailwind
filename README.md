# flask_5_tailwind

### Link to the deployed app: https://stephen-cdn-flask.azurewebsites.net/

## Design Rationale and Principles Followed
### I used the code provided in the lecture as a starting point and then modified it to include a video instead an image and that the design is responsive on both web and mobile.

## Cloud CDN & Video Hosting
1. Sign in Azure.
2. Go to `Storage Accounts` and create a new storage account.
3. Go to `Overview` and click on `Security`. Enable the following:
    - `Secure transfer required`
    - `Allow Blob anonymous access`
    - `Allow storage account key access`
4. Go to `Containers` and create a new container. Set the access level to `Container (anonymous read access for containers and blobs)`.
5. Go into the new container and upload the video file.
6. Go to `Front Door and CDN` and create a new endpoint using the following configurations:
    - `Service type`: `Azure CDN`
    - `Query string caching behavior`: `Ignore query strings`
7. Once the endpoint is deployed, click on click an open a new tab using the endpoint hostname link.
8. In the first tab, go back to `Containers` and click on the container you created earlier. Then, click on the video file url and copy everything after `.net/`.
9. Go back to the new tab opened in step 7 and paste the url after `.net/`. The video should now be displayed on the page. Copy this url as it will be used in the `index.html` file.

## Deploying Flask App to Azure App Service
1. Open up Google Cloud Shell.
2. Clone the repository using `git clone` and `cd` into the repository. Then design the flask app.
3. Add a `requirements.txt` file using `pip freeze > requirements.txt`.
4. In the terminal, run `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash` to install Azure CLI.`
5. Run `az login` and follow the instructions to login to Azure.
6. Run `az webapp up --resource-group <resource-group> --name <app-name> --runtime PYTHON:3.9 --sku B1` to deploy the app to Azure App Service. Replace `<resource-group>` with the resource group name and `<app-name>` with the app name.
7. After the deployment, go to Azure and click on `App Services`. Then, click on the app you just deployed and click on the the link under `Default domain`. The app should now be displayed on the page.

## Observations and Benefits of using a CDN and Cloud Deployment
+ CDN reduces latency and improves performance by caching content in edge servers around the world. This allows users to access the content from the nearest edge server instead of the origin server.
+ Cloud deployment allows the app to be deployed to the cloud and accessed by anyone with an internet connection. It also allows the app to be scaled up or down easily depending on the traffic.

## Challenges Faced
+ I did not experience any challenges while completing this assignment.