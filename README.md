# CloudFormation IAM User and Group Setup

This CloudFormation template sets up an IAM group called "AdminGroup" and three IAM users (AdminUser1, AdminUser2, AdminUser3) associated with this group. Each user is assigned a complex password and requires a password reset upon first login.

## Resources

### AdminGroup

- **Type:** AWS::IAM::Group
- **Properties:**
  - GroupName: "AdminGroup"
  - ManagedPolicyArns:
    - "arn:aws:iam::aws:policy/AdministratorAccess"

This resource creates an IAM group named "AdminGroup" and attaches the "AdministratorAccess" managed policy to it.

### AdminUser1, AdminUser2, AdminUser3

- **Type:** AWS::IAM::User
- **Properties:**
  - UserName: "AdminUser1", "AdminUser2", "AdminUser3"
  - Groups:
    - !Ref AdminGroup
  - LoginProfile:
    - Password: "Set your complex password here" (Password for each user is specified)
    - PasswordResetRequired: true

These resources create IAM users (AdminUser1, AdminUser2, AdminUser3) and add them to the AdminGroup. Each user is assigned a complex password (specified in the template) and requires a password reset upon first login.

## Usage

1. Customize the passwords for each user by replacing the placeholders with strong passwords.
2. Deploy the CloudFormation stack using AWS Management Console, AWS CLI, or AWS SDKs.

## Note

Ensure to securely manage the passwords for the IAM users. Consider using AWS Secrets Manager or Parameter Store for securely storing and managing sensitive data.
