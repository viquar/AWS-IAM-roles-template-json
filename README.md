# AWS-IAM-roles-template-json
Json Template for AWS IAM roles creation



{
  "AWSTemplateFormatVersion" : "2010-09-09",
  "Description" : "My First VPC Subnet",
  "Resources" : {
    "ROLEONE" : {
      "Type" : "AWS::IAM::Role",
      "Properties" : {
        "AssumeRolePolicyDocument" : {
          "Version" : "2012-10-17",
          "Statement" : [ {
                  "Effect": "Allow",
                  "Principal": {
                     "Service": [ "ec2.amazonaws.com" ]
                  },
                  "Action": [ "sts:AssumeRole" ]
               } ]
        },
        "Path" : "/",
        "Policies" : [ {
          "PolicyName" : "root",
          "PolicyDocument" : {
            "Statement" : [ {
              "Effect" : "Allow",
              "Action" : "cloudformation:DescribeStackResource",
              "Resource" : "*"
            }, {
              "Action" : "ec2:*",
              "Effect" : "Allow",
              "Resource" : "*"
            }, {
              "Effect" : "Allow",
              "Action" : "elasticloadbalancing:*",
              "Resource" : "*"
            }, {
              "Effect" : "Allow",
              "Action" : "cloudwatch:*",
              "Resource" : "*"
            }, {
              "Effect" : "Allow",
              "Action" : "autoscaling:*",
              "Resource" : "*"
            }, {
              "Effect" : "Allow",
              "Action" : [ "s3:Get*", "s3:List*" ],
              "Resource" : "*"
            } ]
          }
        } ]
      }
    }
  }
}
