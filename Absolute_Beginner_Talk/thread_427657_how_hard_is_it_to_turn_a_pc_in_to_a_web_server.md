---
title: "how hard is it to turn a pc in to a web server"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by zach12 on 2007-04-29
hello i am new at ubuntu (useing for a few weeks) and would like to use a pc as a web server  
and put a few web site on the web is it hard and can i run apps for ubuntu Desktop on it (i have a laptop too but it would be cool to make web sites on the same computer that keep them on) 
thank you

---

### Post by abcuser on 2007-04-29
Hi,
you need to install web server software and then copy html files to start up folder. You have to know your computer must then run 24/7 to have access to internet. I don't know how important your pages are, but if you have this web page only for your private data, I suggest you try using some free web server on the internet and upload html files, pics etc.
Hope this helps,
Abcuser

---

### Post by Bachstelze on 2007-04-29
As hard as installing a few packages and copying a bunch of files ;)

---

### Post by abcuser on 2007-04-30
zach12,
have you installed web server yet? Try Ubuntu Guide info [ How to install Apache HTTP Server for HTTP (Web) Server service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Apache_HTTP_Server_for_HTTP_.28Web.29_Server_service) - it is very simple.

Hope this helps,
Abcuser

---

### Post by nsleiman on 2007-04-30
thats the wonderful part of linux :) few steps and you can be an administartor :guitar:

---

### Post by zach12 on 2007-04-30
thank you

---

### Post by az on 2007-04-30
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by whee on 2007-04-30
To set-up a server on a machine you need first of all server software.
The most used server software on the internet is calld Apache, it's used by 60%+ of the internet.

Apache can serve basic .html files to clients(browsers) which contain html, javascript and CSS code.
These are all client-side scripts.

If you also want to run server-side scripts like PHP, then you need to download the PHP engine/module.
What you download is basically a php-module for Apache. After that you tell Apache(in it's configuration file) where the PHP engine resides on your machine. When that is done you can add php code to your files.

Lastly you can use a database to store all kinds of data in, the most used database is called MySQL.
With PHP code you can fetch the data out of the database or put data into the database.


All these applications are free and open-source.
If you find downloading and installing all these things a hassle you can try this:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

This is basically a pre-assembled package with all the things you need to run a webserver, things like pointing the PHP-engine location out in the Apache configuration file are already done for you in this package.

---

### Post by bobplano on 2007-04-30
i wouldn't recommend xampp for a real LAMPP because it says on their site it is not very secure but it is fine for local serving and development enviroment

---

### Post by whee on 2007-04-30
> **bobplano said:**
> i wouldn't recommend xampp for a real LAMPP because it says on their site it is not very secure but it is fine for local serving and development enviroment

Good point. Installing Apache, PHP and MySQL yourself is indeed the better option. It also gives you a better understanding of how all these applications work.

---

### Post by koconnor100 on 2007-05-01
> **zach12 said:**
> hello i am new at ubuntu (useing for a few weeks) and would like to use a pc as a web server  
and put a few web site on the web is it hard and can i run apps for ubuntu Desktop on it (i have a laptop too but it would be cool to make web sites on the same computer that keep them on) 
thank you

I would recommend checking with your ISP first. Many of them frown upon you running a web server, and will deliberately block the ports so that you can receive on port 80 ( the default for surfing the net) but not send, effectively killing any home brewed web server right off the top.

---

### Post by zach12 on 2007-05-01
ok

---

### Post by zach12 on 2007-05-01
i use earthlink dsl

---

### Post by bren21 on 2007-05-08
Hey, I first installed xampp, and then decided to uninstall it since it isn't very secure. I then installed apache, php5, and mysql manually using the guide for feisty.  The problem is, when I type in localhost, or localhost/whateverpage it says the url is not found. I am assuming this has something to do with the previous xampp installation. I followed the directions of xampp on how to uninstall it. Anyone know what the problem is?

Edit:
This is what happens when I try to run apache
```

~$  apache2
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/httpd.conf: No such file or directory

```
Line 189
```

Include /etc/apache2/httpd.conf

```
I tried commenting this line out to see what would happen, and the following error occured
```

 ~$  apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

So, does anyone know what the problem is? All help is welcomed and appreciated.

---

### Post by bren21 on 2007-05-09
bump

---

