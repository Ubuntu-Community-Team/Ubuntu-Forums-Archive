---
title: "Slow GRUB boot"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by sjo65 on 2007-02-06
I am a complete Linux noob!  (I just wanted to set that straight ^_^).

I just completed installing Ubuntu 5.10 on my empty hard drive by following some guides on the web.  I made 3 partitions: root, home, and swap.  

I used to boot into Windows XP through a SATA drive, but I added an IDE drive (which is currently set as master) to install Ubuntu onto.  So after I finished installing the kernel, it prompted me if I wanted to add GRUB to my MBR.  

I selected "OK" and then after the system restarted the screen would just freeze (maybe an incredibly long load) on:
"GRUB Loading state 1.5"
"GRUB loading, please wait..."

I'm assuming it has to do something with the drive partitions and master/slave selections, but I have no idea how to fix it. 

Any hints would be appreciated!

---

### Post by sjo65 on 2007-02-06
UPDATE: 

Ok, so I've found out that it's not just GRUB that is slow to start, but the entire Ubuntu boot process.  Each boot process is taking at least 5 min.

---

