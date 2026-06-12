---
title: "cannot deinstall apache2"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-03-05
Hello,

I want to remove Apache 2 and Lamp - so I run this command

sudo apt-get remove apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql && sudo apt-get autoremove

- HOWEVER, /etc/apache2 still exists afterwards.
How is that possible???


So I did rm -r /etc/apach2 - now it removed it.

If I now reinstall apache it recreates the folders, but they are EMPTY!!!


ben

---

### Post by ben22 on 2008-03-05
root@ben-desktop:/etc# sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common php5-common php5-mcrypt
Suggested packages:
  apache2-doc php-pear mysql-doc-5.0 tinyca mysql-server
Recommended packages:
  mailx php5-gd php4-gd
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-auth-mysql libapache2-mod-php5 mysql-client-5.0
  mysql-server-5.0 php5 php5-common php5-mcrypt php5-mysql phpmyadmin
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/43.2MB of archives.
After unpacking 130MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-client-5.0.
(Reading database ... 99912 files and directories currently installed.)
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.45-1ubuntu3.1_amd64.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.1_amd64.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.4-3ubuntu0.1_amd64.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.4-3ubuntu0.1_amd64.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.4-3ubuntu0.1_amd64.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.4-3ubuntu0.1_all.deb) ...
Selecting previously deselected package libapache2-mod-auth-mysql.
Unpacking libapache2-mod-auth-mysql (from .../libapache2-mod-auth-mysql_4.3.9-4_amd64.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.2.3-1ubuntu6.3_amd64.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.3-1ubuntu6.3_amd64.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.2.3-1ubuntu6.3_all.deb) ...
Selecting previously deselected package php5-mcrypt.
Unpacking php5-mcrypt (from .../php5-mcrypt_5.2.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.2.3-1ubuntu6.3_amd64.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.10.3-1ubuntu0.1_all.deb) ...
Setting up mysql-client-5.0 (5.0.45-1ubuntu3.1) ...

Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up apache2-utils (2.2.4-3ubuntu0.1) ...
Setting up apache2.2-common (2.2.4-3ubuntu0.1) ...

Setting up apache2-mpm-prefork (2.2.4-3ubuntu0.1) ...
grep: /etc/apache2/mods-enabled/*.load: No such file or directory
Module cgid does not exist!
This module does not exist!
It looks like you've deleted /etc/apache2/mods-available/cgi.load, so cgi can not be enabled.  To fix this, please purge and reinstall apache2.2-common.
 * Starting web server apache2                                                  apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.

Setting up apache2 (2.2.4-3ubuntu0.1) ...
Setting up libapache2-mod-auth-mysql (4.3.9-4) ...
Setting up php5-common (5.2.3-1ubuntu6.3) ...
Setting up libapache2-mod-php5 (5.2.3-1ubuntu6.3) ...

Setting up php5 (5.2.3-1ubuntu6.3) ...
Setting up php5-mcrypt (5.2.3-0ubuntu1) ...

Setting up php5-mysql (5.2.3-1ubuntu6.3) ...

Setting up phpmyadmin (4:2.10.3-1ubuntu0.1) ...

Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ben22 on 2008-03-05
I reinstalled apache2 commons with synaptic and get the following error:

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1

---

### Post by Vadi on 2008-03-05
Try "sudo apt-get install -f", I think that fixes problems.

---

### Post by ben22 on 2008-03-05
> **Vadi said:**
> Try "sudo apt-get install -f", I think that fixes problems.

what does the  -f mean?

---

### Post by FrozenFox on 2008-03-05
If you type man program_name_here in the terminal/console, it tells all about the program and its options. man apt-get and scrolling a little ways down reveals -f as:

Fix; attempt to correct a system with broken
           dependencies in place. 

(+ lots of other technical stuff, but this is the important part :p)

---

### Post by cybernytrix on 2008-03-28
I am having the same problem. I cannot reinstall no matter what. 
I tried install -f, --reinstall, removed it manually and reinstalled it, nothing helps.

---

### Post by Oldsoldier2003 on 2008-03-28
> **cybernytrix said:**
> I am having the same problem. I cannot reinstall no matter what. 
I tried install -f, --reinstall, removed it manually and reinstalled it, nothing helps.
```

sudo apt-get purge apache2
sudo apt-get clean
sudo apt-get update
sudo apt-get install apache2
```

---

