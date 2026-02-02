📌 PROJECT DESCRIPTION (DETAILED)

This project demonstrates the implementation of a continuous deployment pipeline using AWS managed services. The pipeline automates the deployment of a sample web application hosted on a Windows EC2 instance.

The source code is stored in Amazon S3, and whenever a new version of the application is uploaded, AWS CodePipeline automatically triggers AWS CodeDeploy, which deploys the application to the EC2 instance without manual intervention.

The project showcases real-world usage of IAM roles, S3 versioning, CodePipeline orchestration, and CodeDeploy agent-based deployment on Windows infrastructure.

📌 PROJECT SUMMARY (SHORT & CRISP)

Built an automated CI/CD pipeline using Amazon S3, AWS CodePipeline, and AWS CodeDeploy

Deployed a web application to a Windows EC2 instance

Enabled automatic deployment on every source update

Configured IAM roles and permissions for secure service interaction

Successfully validated deployment via a public web endpoint

📌 STEP-BY-STEP PROJECT EXPLANATION (POINTS)
🔹 Step 1: AWS Console & Region Selection

Logged into AWS Management Console using lab credentials

Selected Asia Pacific (Mumbai – ap-south-1) region

Ensured all services were created in the same region to avoid dependency issues

🔹 Step 2: Amazon S3 Bucket Creation (Source Stage)

Created an S3 bucket to store application source code

Enabled bucket versioning to allow CodePipeline to detect changes

Uploaded the application package SampleApp_Windows.zip

S3 acts as the source repository for the pipeline

🔹 Step 3: IAM Role Configuration

Created an EC2 IAM role with AmazonEC2RoleforAWSCodeDeploy policy

Created a CodeDeploy service role with AWSCodeDeployRole policy

These roles allow secure communication between EC2, CodeDeploy, and CodePipeline without using credentials

🔹 Step 4: Security Group Setup

Created a security group allowing:

HTTP (port 80)

HTTPS (port 443)

Enabled public access so the deployed application can be accessed via browser

🔹 Step 5: Launch Windows EC2 Instance

Launched a Windows Server EC2 instance

Attached the EC2 IAM role created earlier

Associated the instance with the security group

This EC2 instance acts as the deployment target

🔹 Step 6: Install CodeDeploy Agent on EC2

Connected to the EC2 instance using RDP

Installed the AWS CodeDeploy Agent

Verified the agent service was running

This agent allows CodeDeploy to push application files to the instance

🔹 Step 7: Create CodeDeploy Application

Created a CodeDeploy application with:

Compute platform: EC2/On-Premises

Created a deployment group:

Deployment type: In-place

Deployment configuration: AllAtOnce

Linked the deployment group to the EC2 instance using IAM role and instance tags

🔹 Step 8: Create CodePipeline

Created a pipeline with three stages:

Source Stage

Source provider: Amazon S3

Enabled change detection using S3 versioning

Build Stage

Skipped (no compilation required)

Deploy Stage

Deployment provider: AWS CodeDeploy

Linked to CodeDeploy application and deployment group

🔹 Step 9: Pipeline Execution

Pipeline triggered automatically after creation

Source stage pulled the ZIP file from S3

Deploy stage deployed the application to EC2

Pipeline completed successfully with no errors

🔹 Step 10: Application Verification

Accessed the EC2 public IP via browser

Verified successful deployment by viewing the “Congratulations” web page

Confirmed that the application was deployed automatically without manual steps

📌 FINAL PROJECT OUTPUT

✅ Source stage: Succeeded

✅ Deploy stage: Succeeded

✅ Web application accessible via public IP

✅ Fully automated deployment pipeline achieved
