---
title: "System Specs"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-08-28
I was just wondering, how do you view your system specs in ubuntu, like you would in windows?

Edit: I'm mainly looking to find my gfx chipset.

---

### Post by meng on 2006-08-28
There's System > Admin > Device Manager

---

### Post by mcduck on 2006-08-28
in terminal, 'glxgears -info' might tell your graphics chipset. You can also try 'lspci -v'

Other than those, there's plenty of information under /proc so you can for example run 'cat /proc/cpuinfo', 'cat /proc/meminfo' or 'cat /proc/version' to get some usefull info about your system.

Then there's 'free -m' to show info about memory usage (look at the '+/- buffers/cache'-line!) and 'top' to show info about running processes (press 'q' to quit).

---

### Post by meng on 2006-08-28
I thought the poster wanted it done "like in Windows"!

---

### Post by bazcor on 2006-08-28
The newest version of hardinfo might be good. 

[http://hardinfo.klik.atekon.de/](http://hardinfo.klik.atekon.de/)

---

