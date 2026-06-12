---
title: "Mysql Problem"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by apachesoul on 2005-07-15
Hi all,

My problem is I can't connect mysql. I installed it by using synaptic package manager and I gave username and password for it from terminal:

"mysqladmin -u:root -p:root"  - or sth like that, it was working anyways

but after my  phpmyadmin installation I get this error :(

cannot load mysql extension;
please check PHP configuration
Documentation

Bye the way my 2nd question is how can I install a program that not listed in synaptic p.m. (for example php5)

Thanks for your help...

---

### Post by stevenyu on 2005-07-15
check if you have install the php extension for mysql, as well as the php and mysql extension for apache

---

### Post by apachesoul on 2005-07-15
[QUOTE=stevenyu]check if you have install the php extension for mysql, as well as the php and mysql extension for apache[/QUOTE]
 The things that I've installed from syn.pac.man. are below. Aren't they enough? I was using Apache2triad in windows? Isn't there any packet does same thing?

APACHE
-----------------------------------------
Apache2
Apache2-common
apache2-mpm-prefork
apache2-utils
libapache2-mod-auth-mysql
libapache2-mod-php4

PHP
-----------------------------------------
php4
php4-common
libapache2-mod-php4

Mysql
-----------------------------------------
libapache2-mod-auth-mysql
libdbd-mysql-perl
libmysqlclient10
libmysqlclient12
mysql-client
mysql-common
mysql-server
python2.4-mysqldb
python-mysqldb

---

### Post by RastaMahata on 2005-07-16
[QUOTE=apachesoul]The things that I've installed from syn.pac.man. are below. Aren't they enough? I was using Apache2triad in windows? Isn't there any packet does same thing?

APACHE
-----------------------------------------
Apache2
Apache2-common
apache2-mpm-prefork
apache2-utils
libapache2-mod-auth-mysql
libapache2-mod-php4

PHP
-----------------------------------------
php4
php4-common
libapache2-mod-php4

Mysql
-----------------------------------------
libapache2-mod-auth-mysql
libdbd-mysql-perl
libmysqlclient10
libmysqlclient12
mysql-client
mysql-common
mysql-server
python2.4-mysqldb
python-mysqldb[/QUOTE]
 i cant see **php4-mysql** in the list ;)

---

