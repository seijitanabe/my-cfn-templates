# my-cfn-templates
## deploy-vpc-and-bastion
### Resources
- a new VPC (10.0.0.0/16) in ap-northeast-1
- 3 public subnet (10.0.1.0/24, 10.0.2.0/24, 10.0.3.0/24)
- a Internet Gateway attached a new VPC
- a Route table, whiche is associated with 3 public subnet and is added a route to a Internet Gateway as the default gateway.
- a Security Group, which allow the flloweing ingresses:
  - from the CIDR IP range (specified by the parameter) to port 22
  - from the CIDR IP range (specified by the parameter) to port 80
  - from the CIDR IP range (specified by the parameter) to port 443

### Parameters
- Name prefix:
  - String, whitch is used as prefixes for all resource names deployed by this CloudFormation stack.
- Allowed external access CIDR:
  - CIDR IP range that is permitted to access the instances. We recommend
    that you set this value to a trusted IP range. (Default: 0.0.0.0/0)
- AMI ID for Bastion host:
  - AMI ID of an EC2 instance for bastion host. (Default: the latest Amazon Linux 2 AMI)
- SSH key pair name:
  - Name of an existing key pair for bastion host.

### Prerequisites
- SSH key pair
  - You need to create a SSH key pair before creating this CloudFomation stack.

### Architecture Diagram
![deploy-vpc-and-bastion-designer.png](/deploy-vpc-and-bastion\deploy-vpc-and-bastion.png)
