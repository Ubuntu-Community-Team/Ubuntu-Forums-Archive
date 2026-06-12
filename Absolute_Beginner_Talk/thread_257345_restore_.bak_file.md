---
title: "restore .bak file?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by blake711 on 2006-09-14
Hello I just installed ubuntu and I was atempting to get my microsoft intellimouse to have full functionality.  I followed a howto online that didn't seem to work..  One step was to make backups of two files.   Here is an example of the command I used. ```
sudo cp /etc/X11/imwheel/startup.conf /etc/X11/imwheel/startup.conf.bak
```  I searched google for how to do this but it just shows a bunch of items dealing with SQL servers.  Any help on how I can restore the above listed file to the backup version.  

Thanks,
Blake

---

### Post by charles.g.moore on 2006-09-14
if you made the copy all you should have to do is restore the original using the cp command:

sudo cp /etc/X11/imwheel/startup.conf.bak /etc/X11/imwheel/startup.conf

---

### Post by blake711 on 2006-09-14
wow fell stupid there.. I even tryed that but after looking at it I had the context incorrect.  I also tryed the filemanager but had no success that way. 

Thanks for the quick reply.

---

### Post by charles.g.moore on 2006-09-14
No prob...

---

