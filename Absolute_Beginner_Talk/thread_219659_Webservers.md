---
title: "Webservers???"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Qwerty_ on 2006-07-20
What things to i need to do to setup a webserver in Ubuntu that can run my-sql and PHP.

Also does anyone know how to set up coppermine on a server? i was having trouble to a remote server but want to set it up to run locallaly on my Ubuntu box.

---

### Post by indytim on 2006-07-20
LAMP (Linux Apache MySQL PHP)

Follow the guide at [https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28Apache%29]("https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28Apache%29")

IndyTim

---

### Post by Klemik on 2006-07-20
Run synaptic, search apache and download all related files to apache, php and mysql. I suggest also downloading phpMyAdmin ([www.phpmyadmin.net](www.phpmyadmin.net)) package for easier mysql management. Apache document root is at /var/www (its useful info coz I was looking for root some time :D) but you can also put it in /home/username/public_html then you access it by [http://localhost/~username](http://localhost/~username).

---

### Post by az on 2006-07-20
This is the page for you:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)


[http://coppermine-gallery.net/demo/cpg14x/docs/index.htm#installation](http://coppermine-gallery.net/demo/cpg14x/docs/index.htm#installation)
The apachephpmysql page will detail the procedure of installing the LAMP stack (use the defaulton in main, Apache2, PHP5 and Mysql5) and create a database for a user.

You should be up and running in a few minutes...

---

### Post by Qwerty_ on 2006-07-20
Thanks for the replies guys i really appreciate it cheers.

---

### Post by Qwerty_ on 2006-07-21
I have another question how do i get access to copy the coppermine files into the /var/www folder? i guess that this is were i am suppose to copy them i suppose...

EDIT: worked out that sudo nautilus

---

