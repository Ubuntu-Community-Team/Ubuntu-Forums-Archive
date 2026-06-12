---
title: "How to Wipe out Mac OS entirely?"
date: 2008-03-01
forum: Apple Intel Users
---

### Post by aof on 2008-03-01
I installed Ubuntu 7.10 on a iMac Core Duo several months ago. Now the problem is that I can not 
boot into mac os anymore. :( Probably because I made three partitions when installing Ubuntu and 
thus caused problem in Boot Camp.

Is is possible to wipe out Mac OS X entirely? I do not use it at all.

Thanks for help.

---

### Post by PooingCavy on 2008-03-01
THis is probably unhelpful...

But please don't!

(I wub mac OS X)

---

### Post by cyberdork33 on 2008-03-01
> **aof said:**
> I installed Ubuntu 7.10 on a iMac Core Duo several months ago. Now the problem is that I can not 
boot into mac os anymore. :( Probably because I made three partitions when installing Ubuntu and 
thus caused problem in Boot Camp.

Is is possible to wipe out Mac OS X entirely? I do not use it at all.

Thanks for help.
I don't know that messing up Boot Camp has anything to do with being able to boot your Mac into OSX. Holding Option on bootup should allow you to select any bootable OS.

If you intend to remove OS X, then I would suggest just completely installing from scratch. You can alternately try using gparted to delete the OSX partition and resize the Ubuntu partition to take up the space (or create a new partition for something.)

---

### Post by aof on 2008-03-01
> **cyberdork33 said:**
> I don't know that messing up Boot Camp has anything to do with being able to boot your Mac into OSX. Holding Option on bootup should allow you to select any bootable OS.

If you intend to remove OS X, then I would suggest just completely installing from scratch. You can alternately try using gparted to delete the OSX partition and resize the Ubuntu partition to take up the space (or create a new partition for something.)

Boot Camp still works. Actually each time when I start the computer I have to hold the Option key. But 
when I choose to boot into OS X, it just give a plain screen with some noises, nothing shows up.  I tried 
single user mode. I found out that it is due to file system problems such as file permissions. I don't know 
whether it is due the presence of Ubuntu or something that changed the file system.

---

### Post by cyberdork33 on 2008-03-01
> **aof said:**
> Boot Camp still works. Actually each time when I start the computer I have to hold the Option key. But 
when I choose to boot into OS X, it just give a plain screen with some noises, nothing shows up.  I tried 
single user mode. I found out that it is due to file system problems such as file permissions. I don't know 
whether it is due the presence of Ubuntu or something that changed the file system.Just boot from your OSX install disc and repair the disk. Hopefully that will get a booting system again. rEFIt is a better method of choosing the OS. You should try it out.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

