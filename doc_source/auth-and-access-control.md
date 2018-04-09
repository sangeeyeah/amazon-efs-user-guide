# Authentication and Access Control for Amazon EFS<a name="auth-and-access-control"></a>

Access to Amazon EFS requires credentials that AWS can use to authenticate your requests\. Those credentials must have permissions to access AWS resources, such an Amazon EFS file system or an Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. The following sections provide details on how you can use [AWS Identity and Access Management \(IAM\)](http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) and Amazon EFS to help secure your resources by controlling who can access them\. 
+ [Authentication](#authentication)
+ [Access Control](#access-control)

## Authentication<a name="authentication"></a>

You can access AWS as any of the following types of identities:
+ **AWS account root user** – When you sign up for AWS, you provide an email address and password that is associated with your AWS account\. This is your *AWS account root user*\. Its credentials provide complete access to all of your AWS resources\.
**Important**  
For security reasons, we recommend that you use the root user only to create an *administrator*, which is an *IAM user* with full permissions to your AWS account\. You can then use this administrator user to create other IAM users and roles with limited permissions\. For more information, see [IAM Best Practices](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users) and [Creating an Admin User and Group](http://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.
+ **IAM user** – An [IAM user](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html) is simply an identity within your AWS account that has specific custom permissions \(for example, permissions to create a file system in Amazon EFS\)\. You can use an IAM user name and password to sign in to secure AWS webpages like the [AWS Management Console](https://console.aws.amazon.com/), [AWS Discussion Forums](https://forums.aws.amazon.com/), or the [AWS Support Center](https://console.aws.amazon.com/support/home#/)\.

   

  In addition to a user name and password, you can also generate [access keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) for each user\. You can use these keys when you access AWS services programmatically, either through [one of the several SDKs](https://aws.amazon.com/tools/) or by using the [AWS Command Line Interface \(CLI\)](https://aws.amazon.com/cli/)\. The SDK and CLI tools use the access keys to cryptographically sign your request\. If you don’t use the AWS tools, you must sign the request yourself\. Amazon EFS supports *Signature Version 4*, a protocol for authenticating inbound API requests\. For more information about authenticating requests, see [Signature Version 4 Signing Process](http://docs.aws.amazon.com/general/latest/gr/signature-version-4.html) in the *AWS General Reference*\.

   
+ **IAM role** – An [IAM role](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is another IAM identity that you can create in your account that has specific permissions\. It is similar to an *IAM user*, but it is not associated with a specific person\. An IAM role enables you to obtain temporary access keys that can be used to access AWS services and resources\. IAM roles with temporary credentials are useful in the following situations:

   
  + **Federated user access** – Instead of creating an IAM user, you can use preexisting user identities from AWS Directory Service, your enterprise user directory, or a web identity provider\. These are known as *federated users*\. AWS assigns a role to a federated user when access is requested through an [identity provider](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html)\. For more information about federated users, see [Federated Users and Roles](http://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html#intro-access-roles) in the *IAM User Guide*\.

     
  + **Cross\-account administration** – You can use an IAM role in your account to grant another AWS account permissions to administer your account’s Amazon EFS resources\. For an example, see [Tutorial: Delegate Access Across AWS Accounts Using IAM Roles](http://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html) in the *IAM User Guide*\. Note that you can't mount Amazon EFS file systems from across VPCs or accounts\. For more information, see [Managing File System Network Accessibility](manage-fs-access.md)

     
  + **AWS service access** – You can use an IAM role in your account to grant an AWS service permissions to access your account’s resources\. For example, you can create a role that allows Amazon Redshift to access an Amazon S3 bucket on your behalf and then load data from that bucket into an Amazon Redshift cluster\. For more information, see [Creating a Role to Delegate Permissions to an AWS Service](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *IAM User Guide*\.

      
  + **Applications running on Amazon EC2** – You can use an IAM role to manage temporary credentials for applications running on an EC2 instance and making AWS API requests\. This is preferable to storing access keys within the EC2 instance\. To assign an AWS role to an EC2 instance and make it available to all of its applications, you create an instance profile that is attached to the instance\. An instance profile contains the role and enables programs running on the EC2 instance to get temporary credentials\. For more information, see [Using Roles for Applications on Amazon EC2](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html) in the *IAM User Guide*\.

## Access Control<a name="access-control"></a>

You can have valid credentials to authenticate your requests, but unless you have permissions you cannot create or access Amazon Elastic File System resources\. For example, you must have permissions to create an Amazon EFS file system\.

The following sections describe how to manage permissions for Amazon Elastic File System\. We recommend that you read the overview first\.
+ [Overview of Managing Access Permissions to Your Amazon EFS Resources](access-control-overview.md)
+ [Using Identity\-Based Policies \(IAM Policies\) for Amazon Elastic File System](access-control-managing-permissions.md)