---
title: "How to start MySQL client"
date: 2011-10-04
forum: Any Other OS
---

### Post by tech291083 on 2011-10-04
Hi,

I have installed MySQL server and MySQL-client using RPM packages on one of my pcs having Fedora 14. I just downloaded these 2 RPMs from MySQL site and save them to desktop and then I just double clicked on each of them and installed them providing my root password when prompted. After installing them both, I used the following commands to verify that they both are installed. Now how do I start MySQL-client? As far as I know it is a GUI-based tool. Am I right? Thanks

```

[root@localhost james]# rpm -qi mysql
package mysql is not installed
[root@localhost james]# rpm -qi mysqld
package mysqld is not installed
[root@localhost james]# rpm -qa| grep -i mysql
MySQL-client-5.5.16-1.linux2.6.i386
MySQL-server-5.5.16-1.linux2.6.i386
[root@localhost james]# rpm -qa| grep -i mysql-server
MySQL-server-5.5.16-1.linux2.6.i386
[root@localhost james]# rpm -qa| grep -i mysql-client
MySQL-client-5.5.16-1.linux2.6.i386

```

---

### Post by tech291083 on 2011-10-04
I do the following to start MySQL server, not sure if this is the right method,

```

[root@localhost ~]# mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 17 to server version: 5.5.16

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> quit
Bye
[root@localhost ~]#

```

---

### Post by tech291083 on 2011-10-05
Looks like I have made a mistake here by assuming that MySQL-client is a GUI tool to manage database design, but it now looks to me that I actually was looking for something similar called MySQL Administrator that I had used few years back and now it seems to have been replaced by a better GUI called Workbench as mentioned on the official MySQL site.

[http://dev.mysql.com/doc/administrator/en/](http://dev.mysql.com/doc/administrator/en/)

>          **MySQL Administrator has reached EOL. See the         [ EOL         notice]("http://dev.mysql.com/support/eol-notice.html"). Please upgrade to         [MySQL         Workbench]("http://dev.mysql.com/downloads/workbench/").**       
 

Sorry that I have confused myself and other here. Thanks.

---

