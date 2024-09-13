Here is the `README.md` file with the detailed instructions:

```markdown
# DevOps Home Task

This repository contains Terraform configuration for setting up a DevOps environment in AWS. This includes creating a VPC, EC2 instance, Network Load Balancer (NLB), Lambda function, and CloudWatch Events.

## Prerequisites

- **Terraform**: [Download and install Terraform](https://www.terraform.io/downloads.html)
- **AWS CLI**: [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- **AWS Account**: Ensure you have an AWS account and necessary IAM permissions.

## Installation

1. **Clone the Repository**

   git clone https://github.com/your-repo-url.git
   cd your-repo-directory

2. **Install Terraform**

   Follow the instructions on the [Terraform website](https://www.terraform.io/downloads.html) to download and install Terraform for your operating system.

3. **Install AWS CLI**

   For detailed installation instructions, refer to the [AWS CLI documentation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).

4. **Configure AWS CLI**

   aws configure

   Enter your AWS Access Key ID, Secret Access Key, region, and output format.

## Configuration

1. **Terraform Configuration**

   The Terraform configuration file is located in `main.tf`. This file includes:

   - **Provider Configuration**: Set the AWS region.
   - **VPC Creation**: Defines the VPC, Subnet, Internet Gateway, Route Table, and Route Table Association.
   - **EC2 Instance**: Launches an EC2 instance with a specified AMI and security group.
   - **NLB and Lambda**: Sets up a Network Load Balancer, Lambda function, IAM role, and CloudWatch Event Rule.

2. **Update Configuration**

   - **AMI ID**: Ensure it matches your AWS region.
   - **Instance Type**: Choose an instance type that suits your needs.
   - **Lambda Code Filename**: Ensure `lambda_code.zip` is correctly named.

## Execution

1. **Initialize Terraform**

   ```bash
   terraform init
   ```

2. **Plan the Execution**

   ```bash
   terraform plan
   ```

3. **Apply the Configuration**

   ```bash
   terraform apply
   ```

   Confirm by typing `yes` when prompted.

4. **Verify Resources**

   Verify created resources in the AWS Management Console or using AWS CLI commands.

## Verification

1. **Check EC2 Instance**

   ```bash
   aws ec2 describe-instances --query "Reservations[*].Instances[*].[InstanceId,Tags]" --output table
   ```

2. **Check NLB**

   ```bash
   aws elbv2 describe-load-balancers --names "devopshometask-nlb"
   ```

3. **Check Lambda Function**

   ```bash
   aws lambda list-functions
   ```

4. **Check CloudWatch Events**

   ```bash
   aws events list-rules
   ```

## Troubleshooting

- **Blank EC2 Instance Name**: Check the `Name` tag in the Terraform configuration.
- **Permissions Issues**: Verify AWS IAM user permissions.
- **Configuration Errors**: Check configurations and ensure required files (e.g., `lambda_code.zip`) are in place.

For more help, refer to the [Terraform documentation](https://www.terraform.io/docs) or the [AWS documentation](https://docs.aws.amazon.com/).
