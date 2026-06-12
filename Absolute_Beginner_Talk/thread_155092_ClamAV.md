---
title: "ClamAV"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-04-04
I installed ClamAV through Synaptic, however, it didn't create a menu option.  What's the command to launch ClamAV?  Thanks!

---

### Post by johnnymac on 2006-04-04
I don't use clamav I use aegis....but you'll find this website helpful it has all the documentation on how to properly use clamav

[http://www.clamav.net/](http://www.clamav.net/)

---

### Post by OMRebel on 2006-04-04
Found that I needed to install clamtk in order to have a GUI.  However, whenever I run freshclam, I get:

root@ubuntu:/home/brad # freshclam
ClamAV update process started at Tue Apr  4 12:07:05 2006
main.cvd is up to date (version: 37, sigs: 46700, f-level: 7, builder: ccordes)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 6, recommended = 7
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
daily.cvd is up to date (version: 1375, sigs: 2140, f-level: 7, builder: sven)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 6, recommended = 7
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)

---

### Post by OMRebel on 2006-04-04
I ended up going with AVG instead.  The HOWTO on here for installing it was much easier.

---

### Post by 4ebees on 2006-05-30
Hi,
For future reference for anyone that comes to this thread, you have to run freshclam as follows:

$ sudo freshclam

this asks for your password and off you go :)

---

