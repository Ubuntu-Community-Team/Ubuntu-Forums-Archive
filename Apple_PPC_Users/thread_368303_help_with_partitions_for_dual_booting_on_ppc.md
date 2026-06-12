---
title: "help with partitions for dual booting on ppc"
date: 2007-02-23
forum: Apple PPC Users
---

### Post by ike368 on 2007-02-23
i'm trying to set up my powerbook g4 so that i can switch between mac os x tiger (already installed), and ubuntu 6.10.  my only fear comes from the idea of somehow messing up my partitions and loosing everything on the mac side of things.  could somebody help me understand how to prepare the partitions on my 100G hard drive so that i wont lose files?  i want to have about 90G for mac and split the rest between linux.
thanks in advance!

---

### Post by kidders on 2007-02-23
Hi there,

Any application you would like to use to resize your existing disk partitons & make some space for Linux will do fine. I wouldn't ever recommend tinkering with partition structures without doing a full backup first though. Of course, if you go to the trouble of doing that, you might as well rewrite your entire partition table from scratch. OSX's disk utility can do that for you.

 > **ike368 said:**
> i want to have about 90G for mac and split the rest between linux.Ubuntu will find that a tight squeeze!

---

### Post by kmoffat on 2007-02-25
I have a problem with cfdisk, which shows no partitions on my 40gig drive, even though gparted shows 4, one unknown type, and /boot, /, and swap partitions. The drive was unbootable, and I was told the owner could not restore from cd, but ubuntu has installed okay using the 'use entire disk' option.

---

### Post by Auria on 2007-02-25
On my computer i followed the following instructions:
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

and everything worked just fine. Of course it's on the terminal so you need not to be scared by it, and making backups is always a good idea.

---

### Post by grazie on 2007-02-25
10G is plenty to get all the necessary Ubuntu partitions installed on. If you enjoy using Ubuntu though, you may find it fills up quite quickly :)

IMPORTANT

Don't use fdisk or cfdisk on Mac disks as they are tools designed to be used with DOS disks. Use mac-fdisk for Mac disks. gparted handles both types of disk correctly. The partition that gparted reports as unkown type is almost certainly the partition map partition and should be locked. Don't try to delete it unless you want to lose all the data on the disk.

---

### Post by kmoffat on 2007-02-25
"Don't use fdisk or cfdisk on Mac disks...."

Thanks, good info!

Probably explains my problems during a couple of failed installs. 
However, since I had no mac os installed I had to try something else. 
I'm very thankful for gparted.

---

