---
title: "[Slow nfs network] via mount -t nfs IP:/mnt/export /home why ??"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-05
[Slow nfs network] via mount -t nfs IP:/mnt/export /home 
why ??
  
What could be the reasons ?
 
( I have again this problem )
I dont use auto.nfs
nothg into /etc/fstab
  
On the export linux box machine, the exports are looking all right.
  
I dont know where it should be coming from ... :confused: 
  
Thank you,  Greetings !

Patrick

---

### Post by andy80 on 2007-09-21
I've the same problem :(

We had no problem with Ubuntu 6.06/6.10.
Starting from Ubuntu 7.04/7.10 we have this problem. Did you fix it in the mean time?

---

### Post by alexn1 on 2007-09-28
I have Ubuntu 7.04 Feisty Fawn and i solved this problem by installing nfs-common package:

*sudo apt-get install nfs-common*

I hope this is ok also for you! :)

Alexn1

---

### Post by patrick295767 on 2007-11-01
there is the howto there :
[http://patrick295767.pa.funpic.org/debian/howtos.htm](http://patrick295767.pa.funpic.org/debian/howtos.htm)
[http://forums.debian.net/viewtopic.php?t=12423&highlight=samba](http://forums.debian.net/viewtopic.php?t=12423&highlight=samba)

---

