ANSIBLE-CMDBUILD
2016/4/8
2016/4/14 UPDATE
- Add  Alfresco/OCS-inventory/CMDBuild-basic-connector installation

AUTHOR: OSS Laboratories Inc.
http://www.ossl.co.jp
Copyright reserved.
LICENSE: Apache 2.0

CMDBuild 2.4 installation playbook
Please refer CMDBuild Technical Manual for details of installation process.
http://www.cmdbuild.org/en/documentazione/manuali
This playbook intend to use for evaluation or development use.
DO NOT USE FOR PRODUCTION ENVIRONMENT.

Prerequisist: Ansible >2.0 installed system
Target system:
 CentOS/RHEL 6/7 64bit minimal installed
 8GB RAM and 100GB storage available are recommended
Login as root to the Target system
Basic configurations can be edited in "hosts" file.
This playbook does NOT include GIS/BIM/Liferay installation.
Tested on CentOS 6.7 and 7.2

Usage:
1. Copy all files to Ansible executable directory
2. Edit "hosts" file and replace "cmdbuild_hostname" to your target hostname or IP address
3. Invoke command;
'''
# ansible-playbook -i hosts site.yml --ask-pass 
'''
4. Playbook is Installing;
- Oracle JDK 1.8
- Postgres 9.4
- Tomcat 8
- CMDBuild 2.4
- CMDBuild Shark
- Alfresco 5.1
- OCS-inventory Server/Agent
- CMDBuild Basic-connector

5. After completed playbook, 
Check Tomcat logs to find "Server startup in XXXXXX ms"
'''
# tail -f /opt/tomcat/logs/catalina.out
'''
6. Access from your browser;
http://TARGET IP:8080/cmdbuild
to start GUI installation for CMDBuild.

7. On GUI setup,
CMDBuild database name: cmdbuild
Create Shark schima: yes
Postgres Host: localhost
Postgres port: 5432
Postgres user: postgres
Password: postgres
Login user: admin
Login password: admin

8. You need further setup for CMDBuild/Shark. Please refer CMDBuild Technical Maunual.
WEB UI: Administration Module > Setup > Workflow Engne
Username: shark
Password: shark

9. if you have something wrong, 
check /opt/tomcat/logs/catalina.out, cmdbuild.log, shark.log
then restart tomcat.
'''
# pkill -9 -f tomcat
# service tomcat start
'''
10. To access Alfresco
http://TARGET IP:10080/share
Login user: admin
Login password: admin

11. To access OCSinventory
http://TARGET IP/oscreports
Login user: admin
Login password: admin
MySQL user: root
MySQL password: db_passwd_root in "hosts" file, default: password

12. You need further setup for Alfresco/OCS-inventory/CMDBuild-basic-connector.
    Please refer CMDBuild Technical Maunual.

Enjoy CMDBuild!

