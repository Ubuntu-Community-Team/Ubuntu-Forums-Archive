---
title: "help configuring apache2 webserver"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-02-28
Hey

Just installed apache2, got it running, and tried to get it stop loading the "what's in this folder" screen, and load the index.* file instead. I can't seem to find out what to do. Looked in the manual, but i i can't find it

Besides that, i might need php5, and mysql. I know how to install and configure? (I think the php5 part will do, but the mysql is a tough thing)

:)

---

### Post by robinlennox on 2007-02-28
I used this tutorial for my Apache2 LAMP install.

Hope this helps: [http://www.howtoforge.com/node/1388](http://www.howtoforge.com/node/1388)

---

### Post by webofunni on 2007-02-28
I think you need to set the directory listing off in the apache configure file

---

### Post by webofunni on 2007-02-28
Otherwise its better to go for xampp if your aim is not to study about web server installation
get xampp from [http://www.apachefriends.org/en/index.html]("http://www.apachefriends.org/en/index.html")

---

### Post by cmol on 2007-02-28
> **webofunni said:**
> I think you need to set the directory listing off in the apache configure file

Looked around the conf file.. Can't find it :-S

---

### Post by webofunni on 2007-02-28
hope this will help you
[http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html]("http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html")

---

### Post by cmol on 2007-02-28
> **webofunni said:**
> hope this will help you
[http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html]("http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html")

Thanks.. ^_^

Just added index.htm to the list, instead of just index.html

so just the php and the mysql now.. I'll do that tomorrow (6 hours till my danish written exam)..

---

### Post by webofunni on 2007-03-01
Install mysql first then configure your php with ./configure --with-mysql

---

### Post by cmol on 2007-03-02
> **webofunni said:**
> Install mysql first then configure your php with ./configure --with-mysql

Feel kind of dum right now.. Didn't get it..

I should run:
sudo apt-get install mysql(versionXXXX)

And after that

sudo apt-get install php5

?

---

