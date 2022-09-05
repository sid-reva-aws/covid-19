# covid-19
**Deploying a covid-19 website on AWS S3**
This section describes how to deploy the angular application and host them in the AWS S3 service.

**Deploy Angular app to AWS S3 service:**
Let’s deploy our angular application to serverless S3 service. In order to continue, you will need an AWS account. You can create a free account on https://aws.amazon.com/console/. 

**Create S3 bucket to deploy website**
Once you have successfully created an account and logged in, you can navigate to S3 under services -> storage option. The first step is to create an S3 bucket name. The bucket name is unique across all AWS account and hence the generic name should not be chosen as it may be possibly taken.

Also, you need to choose the bucket name wisely as S3 exposes the URL in the following format
[BUCKET-NAME].s3-website.[BUCKET-ZONE].amazonaws.com

1. Following the bucket name, you need to select the region. It makes sense to select the region closer to the user’s location which will provide faster application performance to the users. 
2. Let’s click on the Create button to finally create our S3 bucket. Once the bucket is successfully created, you can find it under the S3 bucket list.
3. Click on the newly created bucket and then click on the properties tab. 
4. Click on the “Static website hosting” card to define the entry page and error page for our application.
5. You will see three options there, you need to select “Use this bucket to host a website”. Here, you need to define the index and error document. In our case, we will define both the document as an index.html page.
6. Also, you can see the endpoint URL which will launch the application in the browser.
7. Let’s click Save and hit the browser with the given endpoint URL. At this stage, we are getting the following 403 forbidden errors. The reason is all S3 bucket policies by default are private which will make the application inaccessible to all the users.
8. We can manage the bucket policy under the “Bucket Policy” tab and grant the public access to all the users.
9. First, let’s go to the Permissions tab and click on the Edit button. Here, the following two options “Block public access through new public bucket” and “Block public and cross-account access through new public bucket” are set to true by default. Let’s uncheck them and click Save.
10. Next, you need to apply a policy that will grant anonymous users to access our data. We can copy the following policy and paste it under the Manage bucket policy section. You need to change the bucket name with your current existing bucket in the Resource property of the JSON object.
11.Also, it’s very important to only grant GetObject to the users and not PUT, DELETE, etc any kind of Edit access in order to prevent any security issues.

**Deploy the Angular build**
Now let’s copy the angular build output that we discussed initially in the article generated at the dist path and upload it in S3.
Once the files are successfully uploaded, you can navigate to the S3 endpoint URL and verify the application is up and running
We have just created our first angular app and deployed it in AWS serverless S3.

