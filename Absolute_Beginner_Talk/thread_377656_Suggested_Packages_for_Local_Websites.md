---
title: "Suggested Packages for Local Websites"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by MarkTX on 2007-03-06
[COLOR="Navy"]I've been using Ubuntu for a month or so now and would like to ask for some opinions on Website Development.

What i want to do, is set up a mock web server on my laptop (loaded with Edgy) and be able to create, build, and generally play with web site programming, php, mysql and possibly CGI without actually having to be connected to the net.

What packages would i need to install, and can anyone offer any personal experience on this?

Many thanks[/COLOR]

---

### Post by compiledkernel on 2007-03-06
For a classic LAMP install -- 

Apache2, Mysql, and PHP. 

Apache - sudo apt-get install apache2
PHP - sudo apt-get install php5-common php5 libapache2-mod-php5
Mysql - sudo apt-get install mysql-server mysql-client

refer to the server guide @ [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html) for further information.

---

### Post by gcclinux on 2007-03-06
> **compiledkernel said:**
> For a classic LAMP install -- 

Apache2, Mysql, and PHP. 

Apache - sudo apt-get install apache2
PHP - sudo apt-get install php5-common php5 libapache2-mod-php5
Mysql - sudo apt-get install mysql-server mysql-client

refer to the server guide @ [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html) for further information.

Awesome, thanks for the tip!

Ricardo

---

