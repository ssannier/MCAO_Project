# MCAO Project

## Disclaimers
Customers are responsible for making their own independent assessment of the information in this document.

This document:

(a) is for informational purposes only,

(b) references AWS product offerings and practices, which are subject to change without notice,

(c) does not create any commitments or assurances from AWS and its affiliates, suppliers or licensors. AWS products or services are provided "as is" without warranties, representations, or conditions of any kind, whether express or implied. The responsibilities and liabilities of AWS to its customers are controlled by AWS agreements, and this document is not part of, nor does it modify, any agreement between AWS and its customers, and

(d) is not to be considered a recommendation or viewpoint of AWS.

Additionally, you are solely responsible for testing, security and optimizing all code and assets on GitHub repo, and all such code and assets should be considered:

(a) as-is and without warranties or representations of any kind,

(b) not suitable for production environments, or on production or other critical data, and

(c) to include shortcuts in order to support rapid prototyping such as, but not limited to, relaxed authentication and authorization and a lack of strict adherence to security best practices.

All work produced is open source. More information can be found in the GitHub repo.

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `npx cdk deploy`  deploy this stack to your default AWS account/region
* `npx cdk diff`    compare deployed stack with the current state
* `npx cdk synth`   emits the synthesized CloudFormation template

## Helpful notes

- You might need to have your docker application open to push the image
- You can avoid using the "--profile" parameter if your profile is globally setup

# Prerequisites 

- Have access to the Hugging Face Mistral 8x7B Instruct in Sagemaker

# MCAO Setup Instructions

Create a new ECR Registry

**Container instructions to push docker image**

```
git clone https://github.com/ASUCICREPO/MCAO_Project.git
cd MCAO_Project/Frontend
```
- Click on your created ECR Registry and Click "View push commands"
- Follow the mentioned commands in order
- Store the ECR URI

# Deploy CDK

```
cdk bootstrap --parameters ECRRepoName=<ECR-URI>
cdk synth --parameters ECRRepoName=<ECR-URI>
cdk deploy --parameters ECRRepoName=<ECR-URI>
```

# Instructions to use if running streamlit manually

## Frontend Changes

- Replace the 'functionName' value with the created Lambda Function in Frontend/InvokeLambda.py
- Replace the 'BUCKET_NAME' value with the bucket name containing all the Police Report PDFs in Frontend/utils.py

## Run Application

```
cd MCAO_Project/Frontend
pip install -r requirements.txt
streamlit run app.py
```
