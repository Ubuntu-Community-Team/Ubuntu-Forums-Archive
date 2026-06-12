---
title: "Really want to get Ubuntu to work"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by DEagleson on 2007-08-28
Just want to make sure that Ubuntu would work on my notebook, since i dont want to F*** it up.

My specs are:

Intel Core 2 Duo T2400 2,00 GHz
ATI Mobility X1800 256 mb (Im aware of [X1*** bug]("http://ubuntuforums.org/showthread.php?t=414194"))
2048 mb ram
2x 120 GB HDD

Already got Windows XP and Vista installed, and i really dont want to remove them, so hopefully someone here could help me manage a thriple-boot solution.

(And please dont flame me for having Micro$oft. :( )

---

### Post by 505 on 2007-08-28
Well, first you could try the live CD. See if everything works. If that is the case, it will also work on a regular installation.

To install Ubuntu you need to have a free partition, or better yet, some unpartitioned hard drive space. It might be best to make this using Partition Manager or GParted on the Live CD. After you have created this free space you can start the installation. When dealing with partitions, just select the free space and Ubuntu will divide it into a data partition and swap space. The installation will also setup the multiboot environment. Not sure if it will pick up both Windows'es, but definitely one. After that, it is not difficult to add the other.

---

### Post by aitorcalero on 2007-08-28
> **DEagleson said:**
> Already got Windows XP and Vista installed, and i really dont want to remove them, so hopefully someone here could help me manage a thriple-boot solution.

(And please dont flame me for having Micro$oft. :( )

How do you choose betwen those two Windows now? I guess that GRUB (Ubuntu start manager) will respect it.
Just another suggestion, run a defrag tool, in both windows, to make sure that your disk are OK before install.

By the way, sure it works! ;)

---

### Post by WebSiteGuru on 2007-08-28
Try looking at this post it might help.

[http://ubuntuforums.org/showthread.php?t=187862](http://ubuntuforums.org/showthread.php?t=187862)

Also, Re-partition you harddrive first will be better. Try LiveCD option first before you dive in. And **backup** your harddirve before you start. ;)

---

### Post by xaco1234 on 2007-08-28
haha, an windows user, so baad, no, just kidding it shoud just beeing installing it on a free partition, you're not the only one with windows and ubuntu on there pc ;)

---

### Post by Steve1961 on 2007-08-28
An easy way to do do this would be to first try the Live CD to make sure it works OK on your system.  Then either create the space for a new partition, or just install a third hard drive.  Install Ubuntu to the partition or drive, and either allow grub to install to the mbr of the first drive, or install grub to the Ubuntu partition.  With the second option you could then use the Vista boot loader to boot all your operating systems if you install EasyBCD.

---

### Post by WebSiteGuru on 2007-08-28
> **xaco1234 said:**
> haha, an windows user, so baad, no, just kidding it shoud just beeing installing it on a free partition, you're not the only one with windows and ubuntu on there pc ;)

LMAOL!:lolflag: Not me (see my sig).  ;) Windows went into the trash. :guitar:

---

### Post by DEagleson on 2007-08-28
I have tested the "live ubuntu cd" but it doesent work.

Currently using Vista's boot manager, and i was hoping that it could handle ubuntu too, since i got really bad memories from Grub.
(I cant really use that stuff. :) )

Also, kudos to the fast help here.
Really fast (like lightning fast).

---

### Post by davidjmayo on 2007-08-28
> **DEagleson said:**
> 
ATI Mobility X1800 256 mb (Im aware of [X1*** bug]("http://ubuntuforums.org/showthread.php?t=414194"))


In the link you gave it says install from the Alternate CD
The LiveCD isn't going to work with your vidcard
Install from the alternateCD and follow the advice you have already for partitioning/bootloader
then follow the bug link to get your card configured

The alternateCD is text-based so gets around the ATI Mobility X1800 problem

---

### Post by DEagleson on 2007-08-29
Gonna try the "Alternate CD" of Ubuntu x64.
Hope it will boot and cooperate with M$.

---

### Post by dan171717 on 2007-08-29
r u sure your cd drive isnt the problem


i tryedto nstal xubuntu oneceand the livecd and alt cd never worked, i put in a new cd drive and it worked fine

---

