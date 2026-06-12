---
title: "[SOLVED] Unable to apt-get install"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by zamani on 2008-01-08
Hello.  This is my first thread.

I tried an example:
 sudo aptitude install torcs

and I got this message:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what should I do?

---

### Post by delphiguy on 2008-01-08
is synaptic running? or maybe automatix or something similar?

---

### Post by Raptor45 on 2008-01-08
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This indicates another package manager, such as Synaptic, is active. If you can't determine what program it is, the easiest way around it is to just restart and you should be all set.

---

### Post by zamani on 2008-01-08
You are right.  Synaptic is running.  

Thanks

---

