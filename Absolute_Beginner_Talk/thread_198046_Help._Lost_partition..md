---
title: "Help. Lost partition."
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Marz157 on 2006-06-16
I'm not sure if this is undo-able but heres what happened.

I was trying to dual boot my laptop with ubuntu and windows xp. xp was already installed. I tried using gnome partition editor to make room for Linux partition. I accidentally created a disklabel and now I have no partitions and xp will not boot. 
If anyone has a solution to get my files back it would be greatly appreciated.

---

### Post by aysiu on 2006-06-16
Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by Marz157 on 2006-06-16
Here you go


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$

---

### Post by aysiu on 2006-06-16
Oooh... that looks bad. You're going to need some recovery tools, then.

Maybe these might help?
[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

---

### Post by NandanK on 2007-09-10
I've gotten into the very same jam as Marz157. I was trying to create a new partition for Windows on my HDD with GNOME... And screwed up. I accidentally attached a disklabel to HDD, effectively losing all my partitions!

Is there any way I can recover the data offa my hard disks without screwing up further??? :confused:

Please help..! :(

---

### Post by NandanK on 2007-09-11
Hah... Is there no help one can offer a wayward soul as me??? :lolflag:

---

