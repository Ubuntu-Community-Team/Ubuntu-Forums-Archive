---
title: "questions"
date: 2008-02-07
forum: Apple Intel Users
---

### Post by BomarJr on 2008-02-07
is it possible to do a tripple boot with 10.5, vista, and ubuntu? i've had a little problem installing it an a new 3rd partition i've made through the disk utility. i'm @ school right now so i'll post some info about my new partition tonite. ;)

thnx in advance

---

### Post by Don Gatto on 2008-02-07
Hello,

I don't think that would cause any problems, but you should install Vista first, or you'll have to reinstall Grub just as you install it :)

---

### Post by cyberdork33 on 2008-02-07
> **Don Gatto said:**
> Hello,

I don't think that would cause any problems, but you should install Vista first, or you'll have to reinstall Grub just as you install it :)
You shouldn't install grub to the MBR on a Mac anyway... Checkout the link in my signature about multi-booting on a Mac.

There are quite a few triple-boot guides in this forum. Here is one.
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

---

### Post by Don Gatto on 2008-02-07
Yupp... sorry for misleading.

---

### Post by gobuntu on 2008-02-07
> **cyberdork33 said:**
> You shouldn't install grub to the MBR on a Mac anyway... Checkout the link in my signature about multi-booting on a Mac.

There are quite a few triple-boot guides in this forum. Here is one.
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

Actually, GRUB does not install in the MBR (Master Boot Record) at all ever in any hard disk, because it can't be done.

GRUB needs a Linux partition to install into.

---

### Post by cyberdork33 on 2008-02-07
> **gobuntu said:**
> Actually, GRUB does not install in the MBR (Master Boot Record) at all ever in any hard disk, because it can't be done.

GRUB needs a Linux partition to install into.
Stage1 is normally copied into the MBR. Stage2 (and 1.5 if needed) is installed on a partition.

---

### Post by BomarJr on 2008-02-07
well, i just checked out that guide and i turned out doing everything in the setup, except the difference is that the cd will not boot. everytime gnome tries to start, it repeates in a repetitive cycle. to at the end, come up in a blue screen saying that the display doesn't work and it is likely something bad is going on. this is something that has been happening constantly after 2 7.10 downloads and 4 disks burned. it's really annoying me since i've followed the instructions. 

This was what i did

download and burned ubuntu through disk utility

installed rEFit,

restarted and then i held down options/alt and started from the cd.

i've done this like 8 times now and got the same results.

any help please?

EDIT: ok, i fixed the problem, i used the terminal command for manual and now it's working but i am a little confused. in the guide, it says not to install to hd0 but to ur linux partition. how will i know which one that i am installing is my linux partition?

---

### Post by cyberdork33 on 2008-02-07
> **BomarJr said:**
> installed rEFit,

restarted and then i held down options/alt and started from the cd.You don't have to hold alt at startup anymore if you installed refit... that is what it is for.

> **BomarJr said:**
> EDIT: ok, i fixed the problem, i used the terminal command for manual and now it's working but i am a little confused. in the guide, it says not to install to hd0 but to ur linux partition. how will i know which one that i am installing is my linux partition?
The guide tells you how to get Grub to "search" for the correct partition:
> 
You will then be at the grub command line. You will then want to find where your grub config file is and such by issuing the command:
```
find /boot/grub/stage1
``` If that does not work, try this instead:
 ```
find /grub/stage1
```Keep in mind that you CAN install to the MBR and it will work, you will just to go through rEFIt _AND_ Grub menus to boot Windows.

---

### Post by gobuntu on 2008-02-22
> **cyberdork33 said:**
> Stage1 is normally copied into the MBR. Stage2 (and 1.5 if needed) is installed on a partition.

What I mean is that GRUB complete can not install in the MBR, a Linux partiton is always required.

Furthermore, GRUB can all of it install in the Boot Record of the Linux partition, and, for that matter, the Ubuntu installation asks something of the sort of "Where do you want the GRUB installed?"

I prefer, on an XP machine, all the GRUB in the boot record of the Linux partition (not on the MBR), and so do also some Mac users.

Why split GRUB if it can not fit in the limitted space of a Master Boot Record?

---

