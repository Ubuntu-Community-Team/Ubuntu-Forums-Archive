---
title: "Mounting Problem"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-07-16
I just installed unbuntu and everything seems to be fine...except that my drives are not mounted.  I let the install have its way.  It divided one drive in half.  I can see this partition with the files for unbuntu.  The system shows the other half of the partition and the other drive.  When I click on one of the icons it  tells me that the drives are not mounted, and something about pmount not being able to mount the removeable drive (the drives are not removeable).  I have right clicked and chosen mount drive and get the same message.  

Any suggestions?

Thanx,

Hillbilly

---

### Post by DavidFL on 2006-07-16
> **Hillbilly Tilley said:**
> I just installed unbuntu and everything seems to be fine...except that my drives are not mounted.  I let the install have its way.  It divided one drive in half.  I can see this partition with the files for unbuntu.  The system shows the other half of the partition and the other drive.  When I click on one of the icons it  tells me that the drives are not mounted, and something about pmount not being able to mount the removeable drive (the drives are not removeable).  I have right clicked and chosen mount drive and get the same message.  

Any suggestions?

Thanx,

Hillbilly

Hello.  Can you type or cut and paste the following command in the terminal shell (APPLICATIONS -> ACCESSORIES -> TERMINAL) and post the results along with generally what these drives are for and how you want to use them? :

```

cat /etc/fstab

```

I suspect that the fstab file is not set up correctly.  This file basically tells Ubuntu which drives you have and where to mount (place) them.

---

### Post by Hillbilly Tilley on 2006-07-17
Here are the results

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hd       /media/cdrom0   udf,iso9660 user,noauto     0       0


I am very big newb, basically I have two 80 gig hard drives.  one is empty and the other is partitioned to run xp and unbuntu.  Just curious about why i cannot see any of the hard drives.  i may want to read or write something off of one sometime.

thanx

---

### Post by Sonic Alpha on 2006-07-17
There is a guide to mounting partitions, [here]("http://www.psychocats.net/ubuntu/mountwindows.php").

---

