# ALB--Project-
An Application Load Balancer in AWS distributes HTTP/HTTPS traffic across multiple backend resources using intelligent routing based on request content, improving availability, scalability, and fault tolerance.
# Classic Load Balancer

## :round_pushpin: Introduction: 
I deployed my application on Amazon EC2 instances behind a Elastic Load Balancing – Classic Load Balancer to ensure high availability, scalability, and fault tolerance.

A Classic Load Balancer (CLB) distributes incoming client traffic across multiple EC2 instances running in different Availability Zones. This helps prevent a single server from becoming overloaded and ensures the application remains available even if one instance fails.

## :bulb: Deployment Steps

### Step 1: Launch Three EC2 Instance.

#### **Server-1**
- Instance Name - Server-1
- Select AMI - Amazon linux
- Key pair - firsy-cal-key.pem
- Security group - allow port httpd (80) ssh (22)
- User data script 
```bash
 #!/bin/bash
 yum update -y
 yum install httpd -y
 systemctl start httpd
 systemctl enable httpd
 echo "<h1>Hello World From $(hostname -f)</h1>" > /var/www/html/index.html
```
- Launch instance
  
### **Server-2**
- Instance Name - Server-2
- Select AMI - Amazon linux
- Key pair - firsy-cal-key.pem
- Security group - allow port httpd (80) ssh (22)
- User data script 
```bash
 #!/bin/bash
 yum update -y
 yum install httpd -y
 systemctl start httpd
 systemctl enable httpd
 echo "<h1>Hello World From $(hostname -f)</h1>" > /var/www/html/index.html
```
- Launch instance
  
### **Server-3**
- Instance Name - Server-3
- Select AMI - Amazon linux
- Key pair - firsy-cal-key.pem
- Security group - allow port httpd (80) ssh (22)
- User data script 
```bash
 #!/bin/bash
 yum update -y
 yum install httpd -y
 systemctl start httpd
 systemctl enable httpd
 echo "<h1>Hello World From $(hostname -f)</h1>" > /var/www/html/index.html
```
- Launch instance
  
![Reference Image](./IMG/Screenshot%202026-03-04%20125809.png)

### Step 2: Create Classic Load Balancer.

- Create load balancer
- Classic load balancer
- Create
- Load balancer name - Classic-LB
- Select Avalability Zone
- Select select security group
- Add instance (server-1, server-2, server-3)
- Create load balancer
  
![Reference Image](./IMG/Screenshot%202026-03-04%20125853.png)

### Step 3: Copy DNS Name.

![Reference Image](./IMG/Screenshot%202026-03-04%20130003.png)

### Step 4: DNS name paste on the broswer and hit the IP address.

### **Server-1**

![Reference Image](/IMG/Screenshot%202026-03-04%20130051.png)

### **Server-2**

![Reference Image](/IMG/Screenshot%202026-03-04%20130112.png)

### **Server-3**

![Reference Image](/IMG/Screenshot%202026-03-04%20130133.png)

**Summary**
I deployed a highly available web application in AWS using a Classic Load Balancer, three EC2 instances, a user data script for automation, and a DNS name for access.

First, I launched three Amazon EC2 instances to host the application. During instance creation, I used a User Data script to automatically install and configure the web server (such as Apache or Nginx) and deploy the application code. This ensured that all instances were configured identically without manual setup.

Next, I created a Elastic Load Balancing – Classic Load Balancer and attached the three Amazon EC2 instances to it. The load balancer:

Finally, I used the DNS name provided by the Load Balancer to access the application. Instead of connecting directly to individual EC2 instances, users access the application through the Load Balancer’s DNS endpoint, which improves availability.