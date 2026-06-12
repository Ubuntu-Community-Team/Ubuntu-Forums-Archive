---
title: "About phpadmin"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by hechizera on 2007-06-22
hello,

when I write *127.0.0.1/phpmyadmin* in my browser, there opens a window which offers to open or save some .phtml file instead of opening phpmyadmin screen. how can I get the screen I need not that .phtml file?

---

### Post by hechizera on 2007-06-22
:(

---

### Post by LaRoza on 2007-06-22
Is your server running? Is is set to execute that file extension?

---

### Post by hechizera on 2007-06-22
> **LaRoza said:**
> Is your server running? Is is set to execute that file extension?
no, it isn't.. what should I do to make it execute that file extension? :oops:

---

### Post by LaRoza on 2007-06-22
Is this server running PHP scripts fine?

---

### Post by az on 2007-06-22
Run

sudo tasksel

and pick LAMP.


That will install the web server and the needed components.

---

### Post by hechizera on 2007-06-22
> **LaRoza said:**
> Is this server running PHP scripts fine?

Actually I have just installed it with this command:

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

+I have restarted them, then when I wrote [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) in my browser it did the thing I wrote about before. I don't really know much about scripts and everything yet. I'd be very grateful if you'd tell me what I haven't done.. :oops: please

---

### Post by trak87 on 2007-06-22
Apache2 needs the php module installed. Okay you did that. I believe I had to make sure these lines where enabled in /etc/apache2/mods-enabled/php5.conf:

```
AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps
```

And then /etc/apache2/mods-enabled/dir.conf needs

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```

Then restart apache2 and test.

---

### Post by mendingo84 on 2007-06-22
hello,

you have a typo :)
it's ```
http://localhost/php**my**admin
```

[edit]or am i wrong?[/edit]

---

### Post by hechizera on 2007-06-22
> **az said:**
> Run

sudo tasksel

and pick LAMP.


That will install the web server and the needed components.

This didn't work :( I mean I chose lamp and pressed enter and it did nothing (only returned me back to terminal line)

---

### Post by hechizera on 2007-06-22
> **trak87 said:**
> Apache2 needs the php module installed. Okay you did that. I believe I had to make sure these lines where enabled in /etc/apache2/mods-enabled/php5.conf:

```
AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps
```

And then /etc/apache2/mods-enabled/dir.conf needs

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```

Then restart apache2 and test.
all of these lines are enabled..

---

### Post by hechizera on 2007-06-22
> **mendingo84 said:**
> hello,

you have a typo :)
it's ```
http://localhost/php**my**admin
```

[edit]or am i wrong?[/edit]
hi,
well yes I type [http://localhost/phpmyadmin](http://localhost/phpmyadmin) or 127.0.0.1 instead of localhost but it still returns some .phtml file :(

---

### Post by hechizera on 2007-06-22
people, maybe you know a good manual on installing apache, php, and mysql? :(

---

### Post by az on 2007-06-22
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Exactly what version of apache do you have installed?

dpkg -l |grep apache

also run

sudo /etc/init.d/apache2 restart

and post the output.

---

