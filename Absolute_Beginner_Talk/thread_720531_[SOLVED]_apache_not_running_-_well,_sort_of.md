---
title: "[SOLVED] apache not running - well, sort of"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by thepiston on 2008-03-10
I installed everything perfectly last night at home, but I didn't want desktop installed so I reinstalled today at work.  Now I can't get to the server from my other PC.  Everything should be running perfectly, but when I go to [http://clardes/](http://clardes/) nothing happens.  I can't use IP address either.  Webmin is installed but that doesn't come up either with [https://clardes:10000/](https://clardes:10000/)

this is killing me - i'm so frustrated right now.  Anyone know what's going on here???

---

### Post by elpichi on 2008-03-10
when it worked before you removed the desktop did you open any ports in the firewall? ussually for apache i had to open port 80 in order to access it remotely. not sure if webmin uses that port also o.o.

---

### Post by thepiston on 2008-03-11
solved - was a network issue, not ubuntu issue

---

