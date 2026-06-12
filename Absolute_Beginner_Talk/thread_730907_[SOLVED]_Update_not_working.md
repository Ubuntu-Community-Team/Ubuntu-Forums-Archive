---
title: "[SOLVED] Update not working"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by ryandufc on 2008-03-21
Followed the update manager to install 2 files - libkrb53 and unzip

I get this- E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Tried running dpkg --configure -a in Terminal and it says I have to be a superuser to do it.
Do I need these updates?

---

### Post by legend2440 on 2008-03-21
Have you tried in terminal
sudo dpkg --configure -a

---

### Post by Shabbro on 2008-03-21
> Tried running dpkg --configure -a in Terminal and it says I have to be a superuser to do it.
Do I need these updates? 

To be a super-user you need to run the 'sudo' command infront of the command you want to use. as in

> sudo dpkg --configure -a  

Then enter your root password.

---

### Post by ryandufc on 2008-03-21
Thanks very much guys, sudo worked first time, all is well,

Thanks again.

---

