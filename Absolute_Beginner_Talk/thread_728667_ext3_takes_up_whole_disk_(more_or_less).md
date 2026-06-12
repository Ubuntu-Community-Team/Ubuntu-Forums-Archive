---
title: "ext3 takes up whole disk? (more or less)"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by genotype on 2008-03-19
Hi All,
I have 2 drives, a 60gb with a windows installation and a 250gb with Ubuntu. I went with the guided install of Ubuntu and am trying to figure out how to format partitions on the 250gb drive that both Ubuntu and Windows can use for MP3s, videos, etc. Currently an ext3 partition is taking up all free space on the 240gb drive and I can't shrink it with gparted. Also, do the common partitions need to be FAT32 to accomplish the above?

 fdisk -l info:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5c8f175

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7476    60050938+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a987723

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14992    77953628    b  W95 FAT32

Thanks for help, much obliged. Also, sorry if I posted this without searching enough (I did look, honest!).

-Gene

---

### Post by Rocket2DMn on 2008-03-19
Actually, any of those filesystems will work.
Windows can read/write ext2/3 with this driver: [http://fs-driver.org/](http://fs-driver.org/)
Both Windows and Linux read/write FAT32 by default (4GB file size limit!)
Linux can read/write NTFS with the ntfs-3g driver which comes preinstalled in Ubuntu Gutsy and newer.

---

### Post by Xiong Chiamiov on 2008-03-19
I find it odd that you can't shrink your ext3 with GParted, since I've never had a problem (so that needs more looking into).  And, though I think it's a relatively new feature, you can read and write to ntfs partitions in Linux, so I can access all of my Windows stuff while in Kubuntu.  Sorry that I can't provide more useful information.

> **genotype said:**
> 
Thanks for help, much obliged. Also, sorry if I posted this without searching enough (I did look, honest!).


And thank you very much for that.

---

### Post by hyper_ch on 2008-03-19
well, you have to use gparted from the LiveCD because your filesystem is mounted...

Fat32 is one way to access files from both... ntfs-3g will enable read/write from linux, [http://www.fs-driver.org](http://www.fs-driver.org) has drivers to access ext3 from windows...

---

### Post by Sef on 2008-03-19
> Currently an ext3 partition is taking up all free space on the 240gb drive and I can't shrink it with gparted. 

You should be able to shrink it.  What happens when you try to shrink the partition with GParted?

---

### Post by genotype on 2008-03-19
It doesn't give me the option to shrink it. The partition has a padlock icon next to it. I have a screen shot...

---

### Post by mikewhatever on 2008-03-19
> **genotype said:**
> It doesn't give me the option to shrink it. The partition has a padlock icon next to it. I have a screen shot...

Perhaps the problem is that you are trying to shrink it while running Ubuntu, and you can't resize a mounted partition. Try using GParted Lice CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jordanmthomas on 2008-03-19
> **mikewhatever said:**
> Perhaps the problem is that you are trying to shrink it while running Ubuntu, and you can't resize a mounted partition. Try using GParted Lice CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

gparted is also on the Ubuntu CD in case you don't have any more CDs laying around.

---

### Post by genotype on 2008-03-20
FAT32 has a 4gb limit? Yikes, didn't know that. I'll try booting to LiveCD, didn't think of that in my panic/petulance.

Thanks for all the help so far.

---

### Post by jordanmthomas on 2008-03-20
[COLOR="Silver"]> **genotype said:**
> FAT32 has a 4gb limit? Yikes, didn't know that. I'll try booting to LiveCD, didn't think of that in my panic/petulance.

Thanks for all the help so far.

That's 4 GB per file.  For me, this is still an issue, but it seems like you may think it's 4 GB total.[/COLOR]

edit
nevermind, I don't think you think that after re-reading.

---

### Post by genotype on 2008-03-20
Right, I was thinking per file. I've downloaded games that have had more than > 4gb installs. Now I know why they split them up sometimes.

---

