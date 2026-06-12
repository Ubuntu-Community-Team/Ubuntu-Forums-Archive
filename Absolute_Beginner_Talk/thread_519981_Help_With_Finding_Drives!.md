---
title: "Help With Finding Drives!"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-08-07
i use alot of programs that need the /dev directory of my diffrent drives, ive been using gparted to find them for now, but it dosent show all of them. is there a program his will tell me what directory my driver are in?

---

### Post by milosz.galazka on 2007-08-07
Hi, Could you precise or give any example?

*mount* command will show mounted filesystems
*dmesg* will show bootup messages so you can find all hard disk devices for example
*cat /proc/partitions*  will show you partitions, you will find a lot of useful info in that director
*cat /etc/fstab* for saved mount points

---

