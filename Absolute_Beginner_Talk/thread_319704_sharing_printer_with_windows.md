---
title: "sharing printer with windows"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by quickk on 2006-12-16
Hi everyone, 

  I just spent three hours trying to do this.  It's driving me crazy!   I'm trying to share my HP psc 2175 printer that's connected to my ubuntu 6.10 machine with a windows XP laptop.   On the laptop the printer is installed.   I managed to get samba working (I think), and I can see the printer in the network.   In windows, I go to add a new printer, select "network printer", it finds the printer, and then it says that it will automatically install the printer drivers.  

At this point, it fails saying that the drivers are not found on the cups server.  I then try to point to my local drivers, (what was left over from the HP printer software installation) and it never works (it keeps on saying that it isn't the right drivers).  

How can I use my local XP drivers instead of trying to install the drivers from the cups server?

Any help would be greatly appreciated!

Another printer question: in Ubuntu, how can I set the default print mode to "draft?"

---

### Post by xyz on 2006-12-16
Would this help:
[by Tammy Fox]("http://www.linuxheadquarters.com/howto/networking/samba.shtml")
Check the " Print Sharing from Linux to Windows" section.

---

### Post by hyper_ch on 2006-12-16
I assume the printer has no ethernet port?

---

