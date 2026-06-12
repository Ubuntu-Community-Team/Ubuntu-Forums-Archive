---
title: "Free partitioning programs?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Willson on 2006-07-07
I am about to install ubuntu soon but i am backing up some data on a slave hard drive right now. When i try to partition it in windows it will onnly allow me to select NTSF, and i want it to be FAT32. 

Is there a free program out there that will let me partition this hard drive?

---

### Post by PingunZ on 2006-07-07
fdisk, gparted, ...

you can do it with the livecd 

Grtz PingunZ

---

### Post by aysiu on 2006-07-07
I would highly recommend DiskDrake, which is available on the PCLinuxOS live CD.

---

### Post by Sonofmoog on 2006-07-07
What partitioning program are you using?  The one that runs during Windows setup will not let you create a vfat (FAT32) partition bigger than about 32 GB.  I use an old version of Partition Magic which will double that to about 65 GB, but anything over that has to be NTFS.  

You might try partitioning it into multiple drives of 32GB

If you have the Ubuntu LiveCD, you can fireup gparted (System, Administration, Gnome Partition Editor)

If you're working in Linux, make sure the partition is unmounted ..

---

### Post by Willson on 2006-07-07
i was using the windows one, i want the whole drive to be fat 32

---

### Post by Willson on 2006-07-07
> **Sonofmoog said:**
> What partitioning program are you using?  The one that runs during Windows setup will not let you create a vfat (FAT32) partition bigger than about 32 GB.  I use an old version of Partition Magic which will double that to about 65 GB, but anything over that has to be NTFS.  

You might try partitioning it into multiple drives of 32GB

If you have the Ubuntu LiveCD, you can fireup gparted (System, Administration, Gnome Partition Editor)

If you're working in Linux, make sure the partition is unmounted ..

It is an 80GB HD, why can't the whole thing be FAT32? (Instead of just 32GB's)

---

### Post by huwshimi on 2006-07-07
> **Sonofmoog said:**
> What partitioning program are you using?  The one that runs during Windows setup will not let you create a vfat (FAT32) partition bigger than about 32 GB.  I use an old version of Partition Magic which will double that to about 65 GB, but anything over that has to be NTFS.  

You might try partitioning it into multiple drives of 32GB
This is interesting as I have a 120GB HDD that is partitioned as FAT32. Is there something wrong with this?

---

### Post by Willson on 2006-07-07
xi0nblue, How did you partition the whole drive as FAT32? Thanks mate

---

### Post by aysiu on 2006-07-07
Linux partitioning programs will let you make a FAT32 partition as large as you want it. Windows will not let you make one bigger than 32 GB.

---

### Post by Willson on 2006-07-07
Figures... thanks mate

---

### Post by BuffaloX on 2006-07-07
Windows systems cannot handle FAT32 above 32GB. ( not officially )
The file system has a specific format, which determines how the drive is addressed. If the format only allows addressing of 32 GB, and you use more than that it may result in errors and data loss.
a bit like trying to calculate 9 digit numbers on an 8 digit calculator.
It is however possible to extend any fileformat, specifying extra bits for addressing. But it should not be used backwards (windows) unless it has been confirmed to work for the entire address space specified,

Sometimes the industri puts in "artificial" limitations, to separate the market. Forcing the customers to behave in a "desired" way. Like upgrading your product, because you outgrow it.

If this is the case, sometimes it can be circomvented, like maybe Windows cannot create NTFS partitions bigger than 32GB, but they can access them.
Note: I don't know that it can!

You have to be careful what you are doing. ( potential dataloss )

It is very obvious Ext3 and Reiser don't have these problems. They are not artificially limited to satisfy a market segment. They have the ability to adress files up to 8 TB!
But in the future even this may be a limitation requering new formats?

To be fair there can be legitimate reasons to have limitations on filesystems.
A filesystem that can address bigger disks and files wastes a higher percentage of your available space, and may also be a little slower.

---

### Post by Bad Seed on 2006-07-07
I would recommend [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") for that job. Since I discovered this great software I uninstalled Partition Magic on my Windows system.

---

### Post by WirelessMike on 2006-07-07
I recommend [SystemRescueCD]("http://www.sysresccd.org/Main_Page").  I've partitioned 3 harddrives with it and it has always worked flawlessly.

I also recommend using NTFS as a base for the Windows OS, but maybe only 40 to 60 Gig.

Now if you intend to dual-boot, In addition to the above NTFS partition, I typically partition a 40G Linux root partition and the rest /home, both as ext3 (not to mention, of course, a small swap partition).

There's a nice open-source app that makes Windows read and write to ext3 called [Ext2fs]("http://e2fsprogs.sourceforge.net/ext2.html") (yes, I know it says "ext2" and not "ext3," but it works, regardless).

---

### Post by Willson on 2006-07-07
> **BuffaloX said:**
> 

If this is the case, sometimes it can be circomvented, like maybe Windows cannot create FAT32 partitions bigger than 32GB, but they can access them.
Note: I don't know that it can!
Can anyone comment on this?

If a FAT32 drive is bigger than 32GB, Will windows have problems? Possible data loss?

---

### Post by Sonofmoog on 2006-07-07
> **Willson said:**
> 
If a FAT32 drive is bigger than 32GB, Will windows have problems? Possible data loss?

I have three PC's.  Each of them has at least one partition that is 65 GB and FAT32.  I've never had a problem with data loss, running XP or 98.  Where FAT32 drives have problems is in slackspace.  Clusters are so large (32 kb) that you're wasting one byte for every three on the drive.  Otherwise, though, there is no problem.

---

