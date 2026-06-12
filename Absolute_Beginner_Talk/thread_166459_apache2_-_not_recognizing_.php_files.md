---
title: "apache2 - not recognizing .php files"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by kbrown3074 on 2006-04-26
I'm having a problem with my LAMP install.  I updated the apache2.conf file to allow the .php and .phps files.  When you put in the address of a .php file...it brings up a save dialog box.  Same thing happens with an .html file, but it is assuming a .phtml extension.  Any ideas??

---

### Post by localzuk on 2006-04-26
Do you have php installed?

---

### Post by kbrown3074 on 2006-04-26
yup..have php4 currently installed

---

### Post by daniel2501 on 2006-04-26
I don't remember even having to edit apache2.conf to get php working.
Did you install libapache2-mod-php5 (or 4)?

---

### Post by kbrown3074 on 2006-04-26
i followed some online directions i found...below is what i did in that order.  It worked for the one guy at work..mine unfortunately isnt working correctly right now.

apt-get update
apt-get install php4 
vim /etc/apache2/apache2.conf
(uncomment the following:)
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
(save the file)
/etc/init.d/apache2 restart
apt-get install mysql-server
/usr/bin/mysqladmin -u root password your_db_user_password
apt-get install libapache2-mod-auth-mysql
apt-get install php4-mysql

---

### Post by localzuk on 2006-04-26
You have not installed libapache-mod-php4

---

### Post by adamkane on 2006-04-26
Breezy:

```

sudo apt-get install apache2 php4 mysql-client mysql-server libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin

``` 
Dapper:
 
 ```

 sudo apt-get install apache2 php5 mysql-client mysql-server libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin

``` 
These are the standard installs.

---

### Post by kbrown3074 on 2006-04-26
Nope..those didnt work either.  I am missing something in a config file?  Everytime I try to bring up a page it still brings up the save dialog box...argh..this is frustrating...

---

### Post by adamkane on 2006-04-26
Yes, it's very frustrating. You need to find a howto and follow it. If you pick the wrong apps, then be prepared to re-install Ubuntu and start over. 

It's very difficult to re-install LAMP, once you've installed a mixed configuration. This happens to everybody. Find a howto that works for you and stick to it.

---

