---
title: "installing Oracle 10G express edition on Dapper Server, success!"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by jasonyu on 2006-06-08
**-------------------Installation with X window ------------------------**
First I installed Kubuntu with KDE desktop on vmware, 

and can download the oracle express for Debian, here: [http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html](http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html)

the installation is rather simple. just use the command:
dpkg -i oracle-xe-universal_10.2.0.1-1.0_i386.deb

run /etc/init.d/oracle-ex configure to configure the database,
There will be a few questions about configuration, you can just accept the default values;
After the installation, there will be some new items in the application menu, from which you can manange the database;
**-------------------Installation with X window ------------------------**



**-------------------Installation without X window ------------------------**
First I installed a Lamp server using Dapper, and use the same installation file of Oracel. If you are using a vmware I recommend you take a snap shot of the virtual machine, or finish reading the words before you continue.

There are something else to be installed to make sure your oracle installation is valid:
If you continue installing Oracle, you will be alerted by a few errors and the oracle installed could not be used.
first you need libaio and libaio1, which can be installed from the repository(archive.ubuntu.com as the source), and one  more thing "bc" is needed to complete the installation. you can download this utility from [http://ftp.jp.debian.org/debian/pool/main/b/bc/bc_1.06-19_i386.deb](http://ftp.jp.debian.org/debian/pool/main/b/bc/bc_1.06-19_i386.deb) or search it from debian's website;

#apt-get install libaio
#dpkg -i bc_1.06-19_i386.deb
#dpkg -i oracle-xe-universal_10.2.0.1-1.0_i386.deb
#/etc/init.d/oracle-ex configure
There will be a few questions about configuration, you can just accept the default values;
**-------------------Installation without X window ------------------------**


**-------------------problems ------------------------**

But after the installation, I can not find a way to manage the database. Because the web management page can not be accessed from an IP address other than 127.0.0.1, but I do not have X installed on this server. And until now, I have not find the right configuration file to change the source IP from which you can access the management website. And this  configure item can be changed from the management website.](*,) 

Finally I installed the oracle client on other machine to manage the server through 1521 port; but I think the management site is enough and it is so convenient and easy to use.

---

