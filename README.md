# AWS-CI-CD-Architecture

Go to AWS CodeCommit , create a Repositorie

Go to IAM , create user

Go to the User you have created and give access to CodeCommit

Go to Security credentials , then go to HTTPS Git credentials for AWS CodeCommit
Generate the credential 

Go to Permissions , Add permissions , Add policies directly , search for codecommit and then add AWSCodeCommitPowerUser

Go to demo-app , go to Clone Url , Clone HTTPS

Make a directory where you can clone  demo-app HTTPS URL
In same directory make a index.html file

Then git add.
git commit -m "added sample file"
git push origin master
(Now index.html file will be there in CodeCommit Repositories)

Go to CodeCommit > Build > Build projects


Choose Mater Branch


Now we will make service role 


Now we have to make Buildspec file 
build file name buildspec.yml

Below buildspec.yml file




version: 0.2

phases:
  install:
    commands:
      - echo Installing NGINX
      - sudo apt-get update
      - sudo apt-get install nginx -y
   build:
     commands:
       - echo Build started on 'date'
       - cp index.html /var/www/html/
   post_build:
     commands:
       - echo Configuring NGINX

artifacts: 
  files:
    -  /var/www/html/index.html



    

git add .
git commit -m "Added buildspec"
git push origin dev


Now Create build project
Go to Build projects > demo-app-build 
Start build

Now go to Edit 
Go to Artifacts
 


Here we have taken  "devops"  from S3 which is bucket already created in S3
Now create folder in "devops" in S3 


Now go to CodeDeploy
Create Applications

Now Create Deployment Group

Enter a service role 

Put In-place Deployment type

Now for Environment configuration you have to create EC2 instances









