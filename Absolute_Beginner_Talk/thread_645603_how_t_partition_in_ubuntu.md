---
title: "how t partition in ubuntu"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by anji454 on 2007-12-20
hi everybody!
iam newbie to linux...i have installed ubuntu 7.10. i have partitioned my harddisk using gparted ..but when iam trying to install windows .it saying that no hardware found...please help

---

### Post by Tux.Ice on 2007-12-20
how did you partition your drive?

i installed windows first then shrunk the partition and then installed ubuntu.

(well thats what i did before, right now i am running only ubuntu 7.10)

---

### Post by finer recliner on 2007-12-20
if you plan on dual booting, it is highly recommended that you install windows FIRST.

---

### Post by Bartender on 2007-12-20
If it was me, I'd download/burn a copy of GPartedLiveCD (GPLCD), which runs like a Linux LiveCD.  Boot from GPLCD, delete all partitions, then create a primary partition at the left end of the partition map.  This would be for Windows.  Once the partition is created, format it as NTFS.  This first partition will be labeled "sda" in GParted, but your Windows CD will recognize it as C:\.  
There are several ways to go as far as setting up the free space on the drive where you want to install Ubuntu.  The simplest would be to set it as a primary partition, then format it to "ext3", then get out of GPLCD.
Install Windows.  Windows should see the NTFS partition as C:\ and install to that partition.  Fire up Windows and see if it works OK.  It should.
Then toss in your Ubuntu CD.  The simplest way to install it - this goes hand-in-hand with the above instructions for "simple" partitioning - would be to let Ubuntu install "Guided" to the sdb partition.  Make sure it installs to sdb, not sda!  sda would be your Windows partition.  Ubuntu will re-format the ext3 section even though it's already ext3 and it'll create a linuxswap partition.

As mentioned, there are all kinds of options when setting up the Linux partition - you could set it up as an extended partition, you could pre-arrange  /, swap, and /home partitions, etc.  But the above is probably the simplest.

---

