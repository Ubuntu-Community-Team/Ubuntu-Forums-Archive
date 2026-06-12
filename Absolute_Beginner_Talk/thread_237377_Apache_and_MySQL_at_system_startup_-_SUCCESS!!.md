---
title: "Apache and MySQL at system startup - SUCCESS!!"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by anroy on 2006-08-16
[FONT="Verdana"]I installed MySQL, Apache and PHP from source tarballs.

Until now I have been starting MySQL and Apache everyday.  It is a real pain.  I had no idea how to make them start automatically but spent most of today investigating how to do this.

This is not meant to be a how-to, but I am just sharing my experience of something going smoothly, in case it helps anyone.

On a Ubuntu 6.06 system...

=========================================
MySQL
=========================================

-----------------------------------------
References Used
-----------------------------------------
[http://www.adobe.com/devnet/dreamweaver/articles/lamp.html](http://www.adobe.com/devnet/dreamweaver/articles/lamp.html)
[http://dev.mysql.com/doc/refman/5.0/en/automatic-start.html](http://dev.mysql.com/doc/refman/5.0/en/automatic-start.html)
[http://dev.mysql.com/doc/refman/5.0/en/mysql-server.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-server.html)
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

-----------------------------------------
Changed in /etc/my.cnf (MySQL site)
-----------------------------------------
[mysqld]
user=mysql

-----------------------------------------
Set startup item (Dreamweaver site)
-----------------------------------------
# sudo cp /usr/local/mysql/share/mysql/mysql.server /etc/init.d/mysql
# sudo update-rc.d mysql defaults

Results of the update-rc.d command were as follows:

Adding system startup for /etc/init.d/mysql ...
/etc/rc0.d/K20mysql -> ../init.d/mysql
/etc/rc1.d/K20mysql -> ../init.d/mysql
/etc/rc6.d/K20mysql -> ../init.d/mysql
/etc/rc2.d/S20mysql -> ../init.d/mysql
/etc/rc3.d/S20mysql -> ../init.d/mysql
/etc/rc4.d/S20mysql -> ../init.d/mysql
/etc/rc5.d/S20mysql -> ../init.d/mysql


=========================================
Apache
=========================================

-----------------------------------------
References Used
-----------------------------------------
[http://www.adobe.com/devnet/dreamweaver/articles/lamp.html](http://www.adobe.com/devnet/dreamweaver/articles/lamp.html)

-----------------------------------------
Set startup item (Dreamweaver site)
-----------------------------------------
# sudo cp /usr/local/apache2/bin/apachectl /etc/init.d/apache
# sudo update-rc.d apache defaults

Results of the update-rc.d command were as follows:

Adding system startup for /etc/init.d/apache ...
/etc/rc0.d/K20apache -> ../init.d/apache
/etc/rc1.d/K20apache -> ../init.d/apache
/etc/rc6.d/K20apache -> ../init.d/apache
/etc/rc2.d/S20apache -> ../init.d/apache
/etc/rc3.d/S20apache -> ../init.d/apache
/etc/rc4.d/S20apache -> ../init.d/apache
/etc/rc5.d/S20apache -> ../init.d/apache


Also, for anyone struggling with installation / environment issues regarding LAMP (Linux/Apache/MySQL/PHP), this article at the Dreamweaver site, of all places, has to be one of the best resources I have found.
[http://www.adobe.com/devnet/dreamweaver/articles/lamp.html](http://www.adobe.com/devnet/dreamweaver/articles/lamp.html)
[/FONT]

---

### Post by Klaidas on 2006-08-16
But if you install LAMP, doesn't it get started automatically and with less work? :)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by anroy on 2006-08-16
> **Klaidas said:**
> But if you install LAMP, doesn't it get started automatically and with less work? :)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
I had to install MySQL and PHP from source because I had to set various custom configure options.  I am writing PHP extensions in C that do MySQL operations.

But that site too looks really good for info about these programs.  

In particular I found the following link there that is right up my alley, I wish I had known about it earlier.
[https://help.ubuntu.com/community/MYSQL5FromSource](https://help.ubuntu.com/community/MYSQL5FromSource)

The corresponding one for PHP doesn't seem to be operational.

I guess I should thoroughly explore the Ubuntu sites before Googling all over the web!

---

