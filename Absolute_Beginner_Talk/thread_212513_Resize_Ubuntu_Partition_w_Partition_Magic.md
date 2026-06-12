---
title: "Resize Ubuntu Partition w/ Partition Magic"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2006-07-10
Will I harm my Ubuntu Partition(damage,corrupt,unbootable) in anyway if I resize it in XP with Partition Magic?

---

### Post by ahaslam on 2006-07-10
Partition Magic will not support Linux filesystems.
Last week I used the Gparted live cd to shrink my Ubuntu partition & create an extra. It worked great, if you have any troubles getting the disc booted see here: [http://ubuntuforums.org/showthread.php?t=209575]("http://ubuntuforums.org/showthread.php?t=209575")

Tony.

*Correction: apparently Partition Magic does support Linux file systems (see post 5). I wouldn't recommend it though, I once had it crash at 50% & lost everything.*

---

### Post by aysiu on 2006-07-10
I would highly recommend DiskDrake, which is available on the PCLinuxOS live CD.

---

### Post by Tristan9669 on 2006-07-10
Everything went ok, but now there is a unallocative space between hda6(ext3) and hda7(swap) and Gparted won't let add it to hda5(ntfs) but it allows me to add it to hda6(ext3) and hda8(vfat), can anyone help?

---

### Post by indytim on 2006-07-10
Just a point of clarification to Tony's posting.  Partition Magic does support ext2 and ext3 formatted partitions.  I pre-formatted my Ubuntu partitions 2 weeks ago using Partition Magic before doing the Dapper clean install.

IndyTim

---

### Post by ilkerka on 2006-07-10
partition magic works but some how linux is not mounting the partition properly. If this is the case do the same operation with Gparted it works perfectly.

---

### Post by Tristan9669 on 2006-07-10
> **indytim said:**
> Just a point of clarification to Tony's posting.  Partition Magic does support ext2 and ext3 formatted partitions.  I pre-formatted my Ubuntu partitions 2 weeks ago using Partition Magic before doing the Dapper clean install.

IndyTim

I did this also, what if I use Partition Magic to move the unallocative space behind the ext3 partition(which allows me to add unallocative space to hda5(ntfs, drive E), would that harm the data on the ext3 partition in anyway?
Here is how it looks
[http://img133.imageshack.us/img133/8709/untitled23xv1.jpg](http://img133.imageshack.us/img133/8709/untitled23xv1.jpg)
[http://img296.imageshack.us/img296/9079/untitled19lp.jpg](http://img296.imageshack.us/img296/9079/untitled19lp.jpg)

---

### Post by karlo on 2008-02-07
> **aysiu said:**
> I would highly recommend DiskDrake, which is available on the PCLinuxOS live CD.

Hmm... that made me curious with **DiskDrake**. Which one is better **gParted** or **DiskDrake**?

---

### Post by forrestcupp on 2008-02-07
I've never used DiskDrake, but I've used GParted Live CD flawlessly.  Also, that is what Ubuntu uses in its installation, so they must think it's good.  I think the problems that people had with GParted in this ancient post have probably been taken care of.  I haven't had any trouble doing anything I need with it.

---

### Post by gladstone on 2008-02-11
GParted all the way here also, but could someone direct me on how to change cluster sizes with a Linux app?

I can't find anyway on GParted to do it and am currently relying on Partition Magic to do the job

---

### Post by louieb on 2008-02-11
> **karlo said:**
> Hmm... that made me curious with **DiskDrake**. Which one is better **gParted** or **DiskDrake**?
Both are good. But DiskDrake can alter the partition table in non-standard way. 
For example You can get it to put a primary partition in the middle of an extended partition. Normally only logical partitions should be inside an extended partition.   I would not think that it would work but it does. The only problem come when you try to use GParted afterward - it sees a non-standard partition setup and gives you a message that there is something wrong with the partition table and won't do anything.

When I need to do partition work I use GParted on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by karlo on 2008-02-11
> **louieb said:**
> Both are good. But DiskDrake can alter the partition table in non-standard way. 
For example You can get it to put a primary partition in the middle of an extended partition. Normally only logical partitions should be inside an extended partition.   I would not think that it would work but it does. The only problem come when you try to use GParted afterward - it sees a non-standard partition setup and gives you a message that there is something wrong with the partition table and won't do anything.

When I need to do partition work I use GParted on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

I see, I also saw 3 GB of disk space, invisible to me, I think it contains ACER files.... 1 GB is free... So I  have 4 partitions?

---

### Post by louieb on 2008-02-11
> **karlo said:**
> ...saw 3 GB of disk space, invisible to me...

:confused:That a confusing statement.  GParted shows that my wifes Acer 5100 laptop has 3 partitions one an Acer recovery, one for VISTA, and one for data.   all a formated to use the NTFS (a Microsoft file system).  

Do you mean GParted shows the partition but you don't see it in Windows explorer? 

Does GParted show it as a partition or unallocated space? 

I can't tell from your description  how many partitions the hard drive has.

DO you have Ubuntu installed or do you have the live CD? if so you can open a terminal **Applications>Accessories>Terminal** and run 
```
sudo fdisk -l 
```(lowercase L) and list the partition table. If you post the output here I could tell if its a partition or unalcated space.

---

### Post by karlo on 2008-02-12
> **louieb said:**
> :confused:That a confusing statement.  GParted shows that my wifes Acer 5100 laptop has 3 partitions one an Acer recovery, one for VISTA, and one for data.   all a formated to use the NTFS (a Microsoft file system).  

Do you mean GParted shows the partition but you don't see it in Windows explorer? 

Does GParted show it as a partition or unallocated space? 

I can't tell from your description  how many partitions the hard drive has.

DO you have Ubuntu installed or do you have the live CD? if so you can open a terminal **Applications>Accessories>Terminal** and run 
```
sudo fdisk -l 
```(lowercase L) and list the partition table. If you post the output here I could tell if its a partition or unalcated space.

Ok THANK YOU! I'll try.. as soon as I solve this issue: [http://ubuntuforums.org/showthread.php?t=692181](http://ubuntuforums.org/showthread.php?t=692181) :lolflag:

---

