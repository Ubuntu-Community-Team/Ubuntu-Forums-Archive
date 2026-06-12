---
title: "installing apache2 on 6.06 desktop"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by richard101 on 2007-05-29
Hi All

I want to install apache 2 on ubuntu 6.06 desktop.
Is there a nice easy walk-through someware please?

thanks

richard101

---

### Post by jasonlfunk on 2007-05-29
> **richard101 said:**
> Hi All

I want to install apache 2 on ubuntu 6.06 desktop.
Is there a nice easy walk-through someware please?

thanks

richard101

The reason it is difficult to find a walk-through is becuase it is so simple. :)

Open a terminal and type

```
sudo apt-get install apache2
```

:popcorn:

---

### Post by richard101 on 2007-06-01
I got this error

"apache2: Could not determine the server's fully qualified domain name, using 127 .0.1.1 for ServerName"

NB: I have a static ip 192.168.0.3 and a web-domain "http://oracle.podzone.org" (that displays a web-page from the dualboot (windows server with iis) on this box) .

I'd like to display apache's default web-page, for now.

---

### Post by joehouse on 2007-09-03
I'm having a similar issue, and unfortunately can't find my new miracle book (I don't remember buying and my wouldn't have a clue to buy it for me) that had walkthroughs for Apache, PHP, and MySQL.  I'll dig through my cars tomorrow to see if it may be in one or the other.  

As soon as I find it I'll post the ISBN for you.  Meanwhile I can only suggest Google.

Apologies,

joehouse "You can't have either too many comics or DVDs."

---

### Post by WorldTripping on 2007-09-03
Try

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Should tidy up your problems.

---

### Post by hyper_ch on 2007-09-03
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)  --> start on page 3 or 4 where it starts with mysql

---

### Post by jingo811 on 2007-09-03
> I want to install apache 2 on ubuntu 6.06 desktop.
Is there a nice easy walk-through someware please?


I went through this during the summer months so I made some notes that worked for me on Dapper 6.06 and Feisty 7.04.  It's not concentrated solely on Apache as you asked but on the whole LAMP package.  So it might not answer your specific questions.
**Desktop LAMP (not Server LAMP)**
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

---

