# AWS and Acronyms
**AWS** - ***Amazon Web Services*** provides a cloud computing platform comprising services under different portfolios like compute, storage, networking, data etc. When it comes to services available, AWS is an ocean and often looks daunting to newcomers. Navigating thru AWS however is easier by adopting structured methods. I will make an attempt to describe the journey by means of Acronyms.
An acronym is a word formed from the first letters or groups of letters in a name or phrase that need to be remembered. It is a memory technique that helps us associate the information we want to remember with a simple shortcut.
Acronyms are dominate any AWS conversation. Everybody uses them, even if they don’t know their name. 

# VM with EC2 of AMI type & attached to 1 or more EBS
We start our AWS acronym journey with a **VM**- ***Virtual Machine***. A virtual machine is a computer with an OS and RAM on which you run your applications. **EC2** -***Elastic compute*** is the service used to create VMs using an **AMI**. **AMI**- ***Amazon machine image*** can be thought of as pre-built template containing the OS to be used along with  applications installed over it. Each **EC2** instance is backed up by a storage in the form of **EBS**-***Elastic Block storage*** which can be attached and mounted as disks to your **VM**. EBS comes in two different flavours- **SSD** ***(Solid state drive)*** and **HDD** ***(Hard disk drive)*** backed volumes. SSD volumes are of type **GP2** - ***General Purpose*** and Provisioned IOPS (**io1**)- Provisioned Input output storage.

# Scale with ASG and distribute load with ALB
EFS- Elastic file system is file storage which can be mounted similar to EBS with the additional capability of being shared across instances. 

# Encrypt with KMS
The storage can be encrypted using AWS or Customer Master Keys (CMK) managed using KMS- Key Management Service. For further control and security over your keys you can use HSM-Hardware Security Module service either from AWS CloudHSM as a managed service or  provisioned from a different provider.

## Create your network-VPC
**VPC**-***Virtual Private Cloud*** is a private network you need to create for running your EC2 instances. A VPC network is created in a AWS region and spans across all **AZ**-***Availability Zones*** within the region. You specify a pool of IP addresses in the form of **CIDR**-***Classless Interdomain routing*** notation. The **VPC** is divided into subnets with IP addresses from the parent VPC. The **EC2** instances are launched within a network and are assigned IP addresses from this pool of IP addresses.You can reserve IPs using **EIP**-***Elastic IP Addresses***.
### Protect your instance with SG and subnet with ACL
You can control traffic for an EC2 instance using **SG**-***Security Group*** where you set up rules for incoming traffic-ingress and outgoing traffic - egress.
However you can control traffic for an entire subnet using **ACL**-***Access Control List***
### Route using Gateways- IGW, LGW, VGW, NAT
Gateways are used to communicate between instances across subnets. You create an **IGW**-***Internet Gateway*** to connect to services in the internet.
### Connect to on-premise systems over VPN or DX
Connect to your on-premise servers using **VPN**-***Virtual Private Network*** or a dedicated leased line ***DX***- **AWS Direct Connect**. VPN is a secure connection over the internet while DX is a dedicated high speed connection between an AWS **POP**-***Point of presence*** and the customer network.
 
# Control acess with IAM
**IAM**-***Identity and Access Management*** is used to manage users, groups and roles by means to policies to allow or deny access to AWS services and APIs. An IAM policy is used to give permission to a user or group. A resource policy is used to grant permission to a AWS resource like a bucket or queue/topic. A **SCP**-***Service Control Policy** is used to draw permission boundaries across one or more AWS accounts. A **STS**-***Security Token Service*** is used to generate a temporary access token to invoke an AWS service either using AWS **SDK**-***Software development kit*** or from AWS ***CLI***-**Command Line Interface**.
 
# Store objects on S3
**S3**-***Simple Storage Service*** is the oldest AWS service used to store objects in containers called **buckets**. You can control access to buckets using resource policies.

# Store relational data with RDS and NoSQL with DDB
**RDS**-***Relational Data Service*** is the managed database offering from AWS. You can choose from Oracle, SQL Server, MySQL, PostGres, MariaDB and Aurora. **BYOL**-***Bring your own License*** option allows you to use your own Enterprise database license instead of using the included license from AWS. This is a managed offering where AWS takes care of things like patching, taking backups and failover. 
**DDB**-***Dynamo DB*** is a nosql global databasefor storing NoSQL data.

# Send message to Queue with SQS and Topic with SNS
**SQS**-***Simple Queue Service*** is used to send message to a **queue** in unordered or **FIFO**-***First in First Out*** pattern.
**SNS**-***Simple Notification Service*** is used to send message to a group of consumers. The sender publishes a message to a **Topic** which is subscribed by 1 or more consumers.
Access to Queues and Topics are managed using resource policies.

# Code your infra with CFN or CDK
**CFN**-***CloudFormation*** rarely called by the acronym is the service to create and update infrastructure by declaring resource configuration in YML files. **CDK**-***Cloud Development Kit*** is a relatively new service for creating infrastructure using populate programming languages like javascript(NodeJS), java, dot net instead of YML files which makes it developer friendly.

# Pull images from ECR to run containers on ECS & EKS
**ECR**-***Elastic Container Registry*** provides a private registry for your docker images with access controlled by **IAM**.
**ECS**-***Elastic Container Service*** is the container orchestration service for running stateless and stateful containers by means of **tasks** and **services**. 
**EKS**-***Elastic Kubernetes Service*** is the managed Kubernetes offering from AWS for running containers.
Both **ECS** and **EKS** come with a fargate option for provisioning EC2 instances in a serverless way.

# Serverless compute with lambda and SAM
**Lambda** is the service for running functions in a serverless model. You provide your function written in one of the supported languages with enough permissions. The server for executing the function is provisioned at the time of invocation. The infrastructure is dynamically scaled depending on the number of concurrent requests. Lambda is commonly invoked by events from other AWS services like API Gateway, SQS, SNS or Cloudwatch.
**SAM**-***Serverless Application Model*** the framework for developing lambda applications with useful tools. 
 
# Monitor/Log with Cloudwatch & Audit with Cloudtrail
These do not have acronyms but among the most important all pervasive services in the AWS portfolio.
**Cloudtrail** captures the audit information who did what and when.
**Cloudwatch** encompasses services for logging,monitoring and event handling. 
 
 # Conclusion
 I tried to provide a beginner level introduction to AWS using acronyms. I covered only the most popular and useful ones from different domains. I hope it will get you excited to dig deeper into AWS. 
