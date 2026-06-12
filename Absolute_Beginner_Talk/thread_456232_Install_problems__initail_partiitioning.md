---
title: "Install problems / initail partiitioning"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by madmist78 on 2007-05-27
System:

160 gb Maxtor HD IDE
AMD Athlon XP 1900+
 1 gb RAM
Asylum 5200 Vid card


I have downloaded ubuntu server 7.04 

When I boot to the cd, I follow all the prompts and inputs until I get to the partiioning section.  I have tried many different  configs, I have tried making a 30gb  primary drive, but after some reading, toned it down to 4gb, but EVERY time that I have completed the partitioning, it gets stuck on the status bar screen" creating ext3 file system"  at 33%   it has stayed this way for hours.


I am not dual booting, as Ubuntu will be the only OS on this system.


Am I missing something?


-madmist78

---

### Post by reacocard on 2007-05-27
> **madmist78 said:**
> System:

160 gb Maxtor HD IDE
AMD Athlon XP 1900+
 1 gb RAM
Asylum 5200 Vid card


I have downloaded ubuntu server 7.04 

When I boot to the cd, I follow all the prompts and inputs until I get to the partiioning section.  I have tried many different  configs, I have tried making a 30gb  primary drive, but after some reading, toned it down to 4gb, but EVERY time that I have completed the partitioning, it gets stuck on the status bar screen" creating ext3 file system"  at 33%   it has stayed this way for hours.


I am not dual booting, as Ubuntu will be the only OS on this system.


Am I missing something?


-madmist78

Try using System -> Administration -> GParted to do the partitioning before you run the install. Sometimes it works better.

---

### Post by madmist78 on 2007-05-27
It looks like GParted is only on the Live cd.  I downloaded the 7.04 server, which does not appear to be a "Live" ISO,   will downloaded the desktop "Live" iso, and see if I can do that...

thanks!

-madmist78

---

### Post by mikewhatever on 2007-05-27
If that drive for Ubuntu only, use the 'format the drive' option.

---

### Post by indigenous71 on 2007-05-27
Unless you want partitions in Ubuntu, you need to use the Ubuntu Partition Editor (which is on Ubuntu Live disk), you then need to delete all partitions so that all the disk is unallocated then just make one large partition, if a partition is locked try changing the formatting. If that doesn't work I'm afriad I can't help you :(

---

