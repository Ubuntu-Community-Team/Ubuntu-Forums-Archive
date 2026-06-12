---
title: "Setting up dual boot partitions"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Mariner51 on 2006-06-21
[FONT="Comic Sans MS"]I am trying to set up a dual boot with Win XP on a 60 Gb hard drive divided in half. My system has 1Gb of dual channel RAM.  I formatted the 2nd  partition as a Reiser, and set the mount point as /boot.. There is 10.5 Mb of free space, which I intend to use as the FAT32 partition. So I went through the same process, to format this, but at the end of it I got the message "The FAT32 file system creation in partition ... failed". If I delete the partition and try to continue with just the Windows NTFS partition and the Linux Reiser partition I get the message: "no root file system is defined".  So – what am I doing wrong?[/FONT]:confused:

---

### Post by kb3hkg on 2006-06-21
You must define the reiser partition as just / not /boot

---

### Post by anaconda on 2006-06-21
Yep..

And you may want to use ext3 instead of Reiser.
Because you can read/write ext3 from windows by installing:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

(and I think ubuntus install defaults to ext3)
So you wouldnt need the fat32 partition at all..

And you may want to make ~500MB swap-partition too. Dont know if it is really necessary with your 1GB of ram.. But it doesnt hurt.. If you dont want to make swap-partition, then you can make a swap-file after installing ubuntu, if you need swap.

---

### Post by stupidkid on 2006-06-21
Try to avoid FAT32 if possible. FAT32 file systems have no file permissions. i.e. all files are rwxrwxrwx. This gets pretty annoying when you open a text file from nautilus and it asks you if you want to execute...-.-

Also FAT32 drives get fragmented really easily since it's such an old fs.

---

### Post by Mariner51 on 2006-06-24
Well that worked OK thank you! I just tried the automatic partition and away it went. Did it agais with Reiser and that worked too. But now I have discovered that the version of Ubuntu that I have (ex magasine cover disk) is actualy 4.1. So I downloaded Dapper Drake: Is there a quick and easy way to upgrade, or do I have to upgrade to 5.1 first? Should it boot from the ISO file I copied to CD?

---

### Post by Apple 101 on 2006-06-24
Just use a burning programme to create the bootable CD from the ISO image.  Make sure that you actually create a bootable CD, not just copy the ISO image onto a blank CD.  You can just upgrade your distribution by using the upgrade install from the CD.

---

### Post by Mariner51 on 2006-06-24
Hey thanks heaps! You have answered two questions in one. I have had problems with ISO files before and wondered why I could not get them to run. From what I have seen of Linux so far I just love it. I can't wait to see it become a total alternative to Microsux!

---

### Post by Frank Golden on 2006-06-24
Hi Mariner,
    I can do almost anything in Ubuntu that I do in XP. The only reason I keep
XP around is I paid good money for It and can't see not using it.

---

