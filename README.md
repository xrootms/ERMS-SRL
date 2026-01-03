# ERMS-SRL
Employee record management system (ERMS) built with Python-Flask and MySQL is a web-based application designed to efficiently manage and track employee data within an organization.


1. ### Setup db:
```bash
#!/bin/bash

sudo apt update
sudo apt install mysql-server mysql-client -y
sudo systemctl start mysql

sudo mysql -u root <<EOF
CREATE USER IF NOT EXISTS 'admin'@'%' IDENTIFIED BY '@1111';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
FLUSH PRIVILEGES;

CREATE DATABASE IF NOT EXISTS srlemployee;
USE srlemployee;

CREATE TABLE IF NOT EXISTS employeetb (
    empid VARCHAR(20),
    fname VARCHAR(20),
    lname VARCHAR(20),
    pri_skill VARCHAR(20),
    location VARCHAR(20)
);
EOF
```

2. ### Setup App:
3. 
```bash
#!/bin/bash
set -e

cd /home/ubuntu

sudo apt-get update -y
sudo apt-get install -y \
 mysql-client \
  python3 \
  python3-pip \
  python3-flask \
  python3-pymysql \
  python3-boto3 \
  git

if [ -d "ERMS-SRL" ]; then cd ERMS-SRL
  git pull
else
  git clone https://github.com/xrootms/ERMS-SRL.git
  cd ERMS-SRL
fi

#edit port 5000, 
#edit config.py (add s3 and rds url)
sudo python3 Empapp.py
```
