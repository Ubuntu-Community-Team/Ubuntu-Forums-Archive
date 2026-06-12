---
title: "How to check the partitions and disks in the system"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by susimetsa on 2007-01-27
I just installed Ubuntu on my laptop and the first thing I'd like to do is to check the disks and partitions and format one of the partitions for Ubuntu's data storage.

However, when I look at the system help, it says:

Check disk space usage and view the partition table

   1     Open  System &#8594; Administration &#8594; Disks
   2.    Select the Harddrive, then the Partitions tab
   3.    Each partition will be listed under Partition List, with disk space and mount point. 

I cannot even complete the first step, because there's no "Disks" option under Administration at all! :confused:

---

### Post by xpod on 2007-01-27
Welcome susimetsa.

If your using edgy 6.10 the "disks" utility which was in dapper 6.06 no longer exists i`m afraid.
The best thing you can do to check and modify partitions is either install "gparted"  or better still download the live cd version of it.

To install it open a terminal ....applications>accsesories>terminal
and type
```
sudo aptitude install gparted
```

That will let you at least view the partitions but you might need to use a cd version of gparted to actually change things.
Theres a "gparted" on the ubuntu live cd  or you can even download it on it`s own live cd  too

Hope this helps

---

### Post by susimetsa on 2007-01-27
Ah! Thank you very much, xpod! :)

Got gparted installed and am now formatting the partition that still needed formatting...

Darn, i feel good being free of the yoke of XP... :)  Still, a lot to be learned of Ubuntu...

---

