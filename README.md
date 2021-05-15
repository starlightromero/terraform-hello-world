# Terraform

Deploying my first Apache web server with Terraform on AWS

## Commands

`terraform init`                     = Initialize Terraform configuration and download any necessary plugins

`terraform plan`                     = Dry run of the code

`terraform apply`                    = Run the code - create the resources

`terraform apply -auto-approve`      = Run the code - create the resources - auto approve all changes

`terraform apply -target RESOURCE`   = Create or modify the specified resource

`terraform destroy`                  = Destroy all resources - alias for `terraform apply -destroy`

`terraform destroy -auto-approve`    = Destroy all resources - auto approve all changes

`terraform destory -target RESOURCE` = Destroy the specified resource

`terraform state list`               = List out all the resources in the current state

`terraform state show RESOURCE`      = Show details for a specified resource

`terraform output`                   = Print all output from terraform file

`terraform refresh`                  = Refresh state and print outputs without adding, modifying, or destroying resources

## Steps

1. Create VPC
2. Create Internet Gateway (allows communication between the VPC and the internet - router)
3. Create Custom Route Table (a database that keeps track of paths, like a map, and uses these to determine which way to forward traffic)
4. Create a Subnet (a network inside of a network - allows traffic to travel a shorter distance without having to pass through unnecessary routers)
5. Associate Subnet with Route Table
6. Create Security Group to allow ports 22, 80, 443 (ssh, http, https)
7. Create a Network Interface with an IP in the Subnet that was created in step 4 (the point of interconnection between a computer and a network)
8. Assign an elastic IP to the Network Interface created in step 7 (a public, static IP address)
9. Create Ubuntu server and install/enable apache2

## Variables

Terraform automatically looks for a file `terraform.tfvars` for any variables defined. To use a custom file name the flag `-var-file` needs to be passed when running the command `terraform apply`.