---
title: "Need HELP with existing RAID"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Aceninja on 2007-05-06
Hi,,

I've got a motherboard with Intel Raid support. On winXP I would use the Intel Matrix manager to configure the RAID 1 Array. I have Ubuntu installed onto a standalone SATA drive and have the RAID 1 array setup in BIOS> However Ubuntu fiesty fawn sees them as two separate drives. How can I get Ubuntu to recognize the already setup RAID 1 array? I do not want to lose any data on the array as it's already set up and working (in windows , I am planning to make it dual boot)

I've been searching for an answer online and cannot find one that is tailored to this particular situation. Can someone help? 

If it type in the terminal ls /dev/mapper I get the following:

control  isw_dacafhih_Raid 1 Data

So what does that mean? That the RAID array is already detected but not mounted?
If so how do I mount it? I am not sure if that is the case though. 

.....losing all hair...plz help :(

---

### Post by nonewmsgs on 2007-05-06
the program you need is mdadm

 [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

hopefully that helps

---

### Post by Aceninja on 2007-05-06
I have mdadm, but how do I use it? Any help would be greatly appreciated :)

---

### Post by nuahs on 2007-05-10
I would like to know the same thing :D
I have just started messing around with ubuntu and would like to do the same thing, ubuntu is installed on a sata drive, and windows was installed on a raid0 array. I would like to mount one of my windows partitions as read only.

---

