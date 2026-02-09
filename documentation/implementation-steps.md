# AWS CloudWatch EC2 Monitoring with Email Alert  
## Detailed Implementation Documentation

---

## Introduction

This project demonstrates the implementation of Amazon CloudWatch monitoring for an EC2 instance and configuring automated email notifications using Amazon SNS when CPU utilization exceeds a defined threshold.

The goal is to enable proactive monitoring and faster incident response.
 
---

## Prerequisites

- AWS Account
- Running EC2 Instance (Ubuntu)
- Basic Linux knowledge
- Email ID for receiving alerts

---

## Step 1: Launch EC2 Instance

1. Login to AWS Console.
2. Navigate to EC2 Dashboard.
3. Launch an Ubuntu Instance.
4. Configure Security Group.
5. Ensure instance state is **Running**.

---

## Step 2: Enable Detailed Monitoring

1. Select EC2 Instance.
2. Click **Actions → Monitor and troubleshoot → Enable Detailed Monitoring**.

This provides more frequent CloudWatch metrics.

---

## Step 3: Create CloudWatch Alarm

1. Open CloudWatch Console.
2. Go to **Alarms → Create Alarm**.
3. Select Metric:


---

## Step 4: Configure Threshold

- Threshold Type: Static  
- Condition: Greater than threshold  
- Value: 40%

This ensures alarm triggers when CPU utilization crosses 40%.

---

## Step 5: Configure Notification

1. Create New SNS Topic.
2. Enter Topic Name.
3. Add Email Address.
4. Click Create Topic.
5. Confirm subscription via received email.

---

## Step 6: Add Alarm Details

- Alarm Name: Email
- Description: CPU monitoring alert

Create Alarm.

Initial state will show **Insufficient Data**.

---

## Step 7: Generate CPU Load

Connect to EC2 via SSH and install stress tool:

```bash
sudo apt update
sudo apt install stress -y

##Run stress command:
##Step 8:Verify CPU Usage
Use:top

stress --cpu 8 --timeout 1000s
##Step 9:Alarm Triggered

CloudWatch changes state:

OK → ALARM
Step 10: Email Notification Received

AWS SNS sends email alert containing:
Alarm Name
Instance Details
Metric Information
Timestamp

EC2 Instance → CloudWatch Metric → CloudWatch Alarm → SNS → Email Notification
