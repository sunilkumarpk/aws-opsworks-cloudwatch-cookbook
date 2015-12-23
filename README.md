# aws-opsworks-cloudwatch-cookbook
This Cookbook will install and configure cloudwatch logs for AWS opsworks instances. 
Read AWS documentation: http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/QuickStartChef.html

<h4>Installation:</h4>
Add these in the layer Setup section.
<ul>
  <li>aws_cloudwatch_logs::config</li>
  <li>aws_cloudwatch_logs::install</li>
</ul>

<h4>Attributes:</h4>
We can configure the logs that we need to send to cloudwatch logs by adding attributes in the json. Add this into the stack configuration to send access, error and mail logs to AWS cloudwatch.

<pre>
{
  "cloud-logs":{
    "1":{
      "type":"access",
      "log_path":"/var/log/nginx/access.log",
      "date_format":"%d/%b/%Y:%H:%M:%S %z",
      "group":"Group name"
    },
    "2":{
      "type":"error",
      "log_path":"/var/log/nginx/error.log",
      "date_format":"%Y/%m/%d %H:%M:%S",
      "group":"Group name"
    },
    "3":{
      "type":"mail",
      "log_path":"/var/log/mail.log",
      "date_format":"%b  %d %H:%M:%S",
      "group":"Group name"
    }
  }
}
</pre>

Inorder to make this work, you must extend your IAM role. For details, read AWS documentation(http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/QuickStartChef.html). 

