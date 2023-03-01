# Terraform EKS
This terraform project performs the following operations:
- Set up an EKS (2 worker nodes) on a dedicated VPC with public and private Subnets
- Create bastion host ASG to access EKS (1 Bastion initially)
- Output the necessary information to query AWS-CLI command to get the kubeconfig of the newly created cluster.



### Create EKS 

Before creating the AWS resources be sure to have the following are ready in your environment:
* Terraform installation 
* AWS Account and keys for that account
* AWS Cli installation
* aws-iam-authneticator



```
terraform apply -auto-approve -var name_prefix=jodel
```

After creating the EKS with the command above, get and integrate the .kubbeconfig to your config file under your home directory.
```
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
```
