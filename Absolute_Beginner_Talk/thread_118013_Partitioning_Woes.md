---
title: "Partitioning Woes"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by ianl on 2006-01-16
hi all, very new to linux/ ubuntu. 

ok, so i have a 80g hdd. i have breezy installed on a partition i created with partitionmagic, around about 30g, a previously installed winxp is on the other 40g, and i have a small 50mb partition that partitionmagic's bootmagic program seemed to desperately need (a bad idea i see now.)  oh and there is also the 1.5gb swap partition that ubuntu automatically set up.  

the thing is i have been trying to install WoW by copying it from my winxp partition, except that i cannot acces the partition from ubuntu, nor can i even see the ubuntu partition from winxp. and now when i try to load partitionmagic in windows it gives me the error "Init failed: error 117.     Partition's drive letters cannot be identified."  The most odd thing though is when i load up the WoW installer it can see both partitions, but cannot install on the linux one because it is invalid, and the drive letter is z: or something crazy.

if this seems like a lost cause just say so and i'll reformat and try it from scratch!

thanks

---

### Post by aysiu on 2006-01-16
[QUOTE=ianl]i cannot acces the partition from ubuntu[/quote] Yes, you can--you just have to see the fourth link of my signature. > nor can i even see the ubuntu partition from winxp. This is normal. Any way that Windows can invalidate Linux, it will. 

> The most odd thing though is when i load up the WoW installer it can see both partitions, but cannot install on the linux one because it is invalid, and the drive letter is z: or something crazy. When you use Wine to install Windows programs in Linux, it assigns Z: arbitrarily to the Linux partition. Thus, I've installed FileZilla to Z:\home\username\.wine\drive_c\Program Files\FileZilla\FileZilla.exe

---

### Post by dueY on 2006-01-16
[QUOTE=ianl]hi all, very new to linux/ ubuntu. 

ok, so i have a 80g hdd. i have breezy installed on a partition i created with partitionmagic, around about 30g, a previously installed winxp is on the other 40g, and i have a small 50mb partition that partitionmagic's bootmagic program seemed to desperately need (a bad idea i see now.)  oh and there is also the 1.5gb swap partition that ubuntu automatically set up.  
[/QUOTE]

That's odd that it made you make a 50mb partition, my PM8 never did that (don't think PM7 did either back in the day).

---

### Post by Sef on 2006-01-16
>  i have breezy installed on a partition i created with partitionmagic

Partition Magic is not always compatible with Linux.  There are numerous posts and threads about its incompatibility.  Better to use GParted which is on the install disk.

---

### Post by dueY on 2006-01-17
[QUOTE=Sef]Partition Magic is not always compatible with Linux.  There are numerous posts and threads about its incompatibility.  Better to use GParted which is on the install disk.[/QUOTE]

I've used multiple versions of Partition Magic on multiple computers and it has always worked fine for me.  Both the Install New OS wizard and manually doing it.

---

### Post by ianl on 2006-01-17
thanks for the replys. love those signature links. in the end i just formatted and straight installed ubuntu. if linux gets to be too much hassle i can always partition again and put it back, it's a lot of work but i think linux may be worth it!

---

