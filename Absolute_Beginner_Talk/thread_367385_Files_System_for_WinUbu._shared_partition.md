---
title: "Files System for Win/Ubu. shared partition"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Janzomaster on 2007-02-22
Hi, I got a partition that I want to share between Windows XP and Ubuntu. Right now, its full of stuff and NTFS.
I know there is a thingy out there that lets you work with NTFS under Ubuntu. But its still Beta, might mess up the whole thing.

Would you recommend changing the files system (backing everything up, formating etc) or rather use the NTFS file system?

FAT32 would be the new file system of choice, right?

---

### Post by Archmage on 2007-02-22
FAT32 has the problem that it can't use files over 4GB size.

The driver ntfs-3g just got out of Beta into 1.0. But it still can't work with compressed or encrypt files nor does is support the NTFS rights.

But for a normal home-user this should be okay to use.

(I'm using it already for three months and did never encounter a problem with it so far.)

---

### Post by george29 on 2007-02-22
I dual boot dapper and XP, if you have the ability to back up everything you want to keep on that partition - then i would recomend that you do so and then format the drive as FAT32 to allow sharing between ubuntu and XP. 

alternatively you could format the partition as Ext3 and then install drivers in your windows install which will allow it to read and write to the Ext3 partition. links below.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

 george

---

### Post by aberry5555 on 2007-02-22
unfortunately, though, it would be difficult to install Ubuntu on to the NTFS partition (without simply copying it across from windows) as ntfs-3g is not installed as standard. You would have to install ntfs-3g on the livecd first, then mount the windows drive and store the settings for mounting it before you start installing it, which is quite long winded and could, I think, cause problems.

---

### Post by Janzomaster on 2007-02-22
Dont worry about Ubuntus file system, he gets his own partition with ext3.

FAT32 only supports up to 4 GB? I thought that was FAT16... Well, been some time since I last used these file systems... Definetly will need support for more than 4GB HDD. So NTFS?

---

### Post by george29 on 2007-02-22
FAT32 filesystem can be used on whatever size partition you like - i have an external drive 320Gb formatted in FAT32 with 3 partitions of 150, 100 and 50Gb so they can be read and written to by both xp and dapper installs on my desktop..

the 4Gb limit is an individual FILE size.

---

### Post by mcduck on 2007-02-22
I recommend Ext3 and then using some Ext2/Ext3 driver in windows to allow Windows to use the partition. It's far more reliable than NTFS drivers for Linux. (and IMHO Ext3 is far better than NTFS ;))

I'm using this one myself: [http://www.fs-driver.org/]("http://www.fs-driver.org/index.html")

---

### Post by Janzomaster on 2007-02-24
Ok, just let me get this right:

1. The driver from fsdriver.com doesnt suppoert UTF8, thus no öäü in my filenames.

2. The chryoscome software doesnt allow me to access the ext3 partition from my exploer etc, only through the software and I cant write onto that partition

Is that right?

---

