---
title: "Can i run PHP Files locally and connect to MySQL databases remotely?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2007-12-30
topic

---

### Post by blueridgedog on 2007-12-30
PHP is a parsed language, so as long as you have a local web server you should be able to access your php script with [http://localhost/myphppage.php](http://localhost/myphppage.php) and it will function (you will need to install apache, php and the apache module).  After that accessing a remote MySQL server is a mater of knowing your php.

You can isntall apache and php with:

apt-get install apache2 php5 libapache2-mod-php5

---

### Post by GGLucas on 2007-12-30
You can, providing that the remote MySQL database server is accepting connections outside localhost, keep in mind a lot of servers are set to that by default, so you'll need to find out how to set it to accept them if you can't connect to it at first.

---

