---
title: "the &quot;service&quot; command."
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by lynxus on 2006-09-18
#-o 

Hey guys.. Im a little stuck.

In fedora core if i wanted to restart the network service, I would type 

Service network restart


This doesnt work in ubuntu ( or using sudo service network restart )

Whats the Ubuntu version of this ? Say i wanted to restart / stop / start the apache webserver .. how do i do this via the command line ?


Cheers
g

---

### Post by chuckyp on 2006-09-18
sudo /etc/init.d/name_of_service stop|start|restart

---

### Post by Brunellus on 2006-09-18
you'd have to do it with the init scripts:

sudo /etc/init.d/network restart

---

### Post by lynxus on 2006-09-18
Thanks guys :)

---

