# Automation with CloudFormation

This repository includes CloudFormation scripts that will help you dpeloy infrastructure in a consistent, reliable manner.

The script will 
  - Deploy an AWS CloudFormation stack with a defined Virtual Private Cloud, and Security Group
  - Configure an AWS CloudFormation stack with an S3 bucket, and an EC2 instance

This is the architecture of the initial step
 
 ![image](https://user-images.githubusercontent.com/40435982/115768879-e3e87f00-a378-11eb-8119-0411f0673752.png)

## About the code inside the script

I will provide a general overview of the code written in this script. If you look throught the file

1. The Parameters section is used to prompt for inputs that can be used elsewhere in the template. The template is asking for two IP address ranges for defining the VPC. 

`AmazonLinuxAMIID:
    Type: AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
    Default: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2`
    
  This parameter specifically uses the AWS systems manager parameter store to retrieve the latest AMI (specified in the defaul parameter, which in this case is Amazon Linux 2) for the stack's region. This makes it easy to deploy stacks in different regions without having to specify an AMI ID for every region.
  
2. The Resources section is used to define the infrastructure to be deployed. The template is defining the VPC, a security group, and S3 bucket as well as an EC2 isntance

3. The Outputs section is used to provide selective information which is commonly used for configuration files. The template is providing the default security group for the VPC that is created.

