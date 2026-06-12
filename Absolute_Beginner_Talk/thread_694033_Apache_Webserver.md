---
title: "Apache Webserver?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by billenium14 on 2008-02-11
I'm a real beginner... So far this is what i have done:

Installed apache2


I'm pretty sure right now, it stops at the router i am guessing. Now, can someone help me with making it so people across the world (anyone with internet) can access it? I don't really want a DNS name either... The ip address ,3.4.5.6.7 or whatever it is, is fine.

So basically, i want to how to let everyone else access it, not just the people connecting to my router.

Thanks so much!

---

### Post by OffAxis on 2008-02-11
you need to forward the 80 port from your router to your computer (with apache2 on it)

so...
1. access your router. Open firefox and input your router's ip. It's usually at 192.168.1.1 or 192.168.0.1

Then input your username/password. if you've never set one up it's something like name: admin password: (nothing)
You can look it up in your router's manual.

2. Forward port 80 in the 'Port Forwarding' section. To find out your computer's ip you can look in the 'attached devices' section or run **ipconfig **on the computer, and it'll tell you.

---

### Post by Mantis86 on 2008-02-11
basically, what you need to do is forward port 80 from your router to your apache webserver

---

### Post by billenium14 on 2008-02-11
I'm using a Linksys router... i see A LOT of options in Port Range Forwarding... Ill upload a picture...

[http://img98.imageshack.us/img98/4541/screenshotya7.png](http://img98.imageshack.us/img98/4541/screenshotya7.png)

---

### Post by jan quark on 2008-02-11
here is what I have done long time ago to set up such a server :)

perhaps it will help you
[http://laiconic.quotaless.com/tutorial2.html](http://laiconic.quotaless.com/tutorial2.html)

---

