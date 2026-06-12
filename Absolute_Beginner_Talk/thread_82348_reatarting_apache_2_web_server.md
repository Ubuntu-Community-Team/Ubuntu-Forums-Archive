---
title: "reatarting apache 2 web server"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by rthewissen on 2005-10-26
Hello,

New to the linux arena. Have installed the latest ubuntu with apache web server.

I am trying to figure out how to restart the apache service without rebooting.

I have seen alot of reference to the apachect1 restart, but the problem is, I can't seem to locate the apachect1.


Help Please!!

---

### Post by davmac on 2005-10-26
Just open a terminal and type "sudo /etc/init.d/apache2 restart"

Hope this helps,

Dave Mac

---

### Post by herrpoon on 2005-10-26
Hi, I actually find that that one doesn't work for me!  I type it in and it doesn't do anything!  It may be more of a problem at my end, but just in case here's what I use:

sudo /usr/sbin/apache2ctl restart

---

### Post by Ride Jib on 2005-10-26
also take note: it is apachect**l**, not apachect**1**

---

### Post by lreyes6 on 2005-10-26
if in a console you do this... sudo ls /etc/init.d/ what do you see? apache2 or apache????

---

