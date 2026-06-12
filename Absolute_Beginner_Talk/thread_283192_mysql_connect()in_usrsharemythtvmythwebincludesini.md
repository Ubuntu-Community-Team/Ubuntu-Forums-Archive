---
title: "mysql_connect()
in /usr/share/mythtv/mythweb/includes/init.php on line 54"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-10-23
Help,

Received the following error when trying to install MythTV (mythtv-setup)


Fatal error: Call to undefined function: mysql_connect()
in /usr/share/mythtv/mythweb/includes/init.php on line 54
when I click on mythtv from localhost


Also, I get
phpMyAdmin - Error
Cannot load mysql extension. Please check your PHP configuration. - Documentation
when I click on phpMyAdmin.

I have the following installed:
apache2-default
mythweb
phpmyadmin


Any ideas. (I'm a complete noob)

---

### Post by ljpm on 2006-10-25
bump.

anyone?

---

### Post by superm1 on 2006-10-26
Lets see.  Which OS are you on, Dapper or Edgy?  Which source are u using for packages to start?

---

### Post by ljpm on 2006-10-28
> **superm1 said:**
> Lets see.  Which OS are you on, Dapper or Edgy?  Which source are u using for packages to start?

oops, sorry.

I am running Dapper. 

I am following this how to.

[http://ubuntuforums.org/showthread.php?t=186747](http://ubuntuforums.org/showthread.php?t=186747)

which is a modification of 

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

---

### Post by superm1 on 2006-10-28
Well for starters, those packages are a bit dated.

If your gonna do dapper, use these packages:

#my myth repo
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main



Although i'd recommend jump up to edgy.  Edgy has packages built in.

---

