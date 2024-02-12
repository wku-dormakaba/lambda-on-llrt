## Introduction

This repo contains the basic setup for deploying an AWS Lambda with Terraform.
It will use the AWS LLRT as the JS runtime on Amazon Linux 2023 (and for this repo, x86_64 architecture).


## Pre-requisites
* AWS profile
* Terraform CLI
* AWS CLI

## Setup
1. At project root folder level, do a `terraform init`.
1. Modify the values at `variables.tf` accordingly.
1. Refactor the lambda code at `src/index.js`. `npm install` etc.
1. `npm run build` to output to `dist`
1. `terraform apply`
1. Rinse and repeat steps 3-5

## Invoke Lambda
Using AWS CLI,
````
aws lambda invoke --function-name=$(terraform output -raw function_name) --profile=<AWS profile> tmp/response.json
```` 
