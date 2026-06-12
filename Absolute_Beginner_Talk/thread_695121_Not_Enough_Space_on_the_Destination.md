---
title: "Not Enough Space on the Destination"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by moose53 on 2008-02-12
I'm a newbie -- EXTREMELY.

Just today installed Ubuntu to dual-boot with Windows ME until I get my files off of Windows.

I'm in the process of moving "My Documents", "My Pictures", etc. to my home directory on Ubuntu.

I'm getting the error "not enough space on the destination" on the last few folders that I'm trying to move.  I'm assuming it's because either the amount of info in the folder or the actual file sizes are too big to retain in memory and also to copy/move to HOME.

Do I need to increase the size of my HOME folder??  Is that even possible??  I know absolutely nothing about Linux or Ubuntu.  I spent over 13 years working on senior help desks for Windows support ... so I'm got a TON of crap to get out of my brain :lolflag:

Thanks.

Barb

PS:  Oh, it looks like I'm using Nautilus 2.18.1 to move the files from Windows ME to Ubuntu (if that makes any difference).

---

### Post by Famicommander on 2008-02-12
How large is your Ubuntu partition, and how large is your hard drive overall?

---

### Post by taurus on 2008-02-12
Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```
Basically, you can reduce the size of your windows partition and give that to Ubuntu.  You need to use gparted from either Ubuntu LiveCD or GParted LiveCD.  

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

And of course, _ALWAYS_ back up those important files on your harddrive before you resizing just in case something might go wrong.

---

### Post by moose53 on 2008-02-12
Excuse the delay -- I had to reinstall Windows ME again -- 5th time in two months.  Hate Microsoft.

OK.

I cannot login to Ubuntu -- get an error message "GDM could not write to your authorization file".

I don't see gparted on the live-disk.  Is it called something else??

System Info:

Description:  Generic IDE Disk Type47
Manufacturer  (Standard disk drives)
Model  IDE Disk Type47
Media Loaded:  Yes
Media Type:  Fixed hard disk media
Partitions  4
Size:  9.42 GB (10,110,320,640 bytes)
Partition:  Disk #0, Partition #0
Partition Size:  5.21 GB (5,593,158,144 bytes)
Partition:  Disk #0, Partition #1
Partition Size:  800.11 MB (838,978,560 bytes)
Partition:  Disk #0, Partition #2
Partition Size:  3.22 GB (3,454,617,600 bytes)
Partition:  Disk #0, Partition #3
Partition Size:  211.79 MB (222,082,560 bytes)

I let the Ubuntu software create the partition.  I'm assuming one is Windows ME, one is Ubuntu, one is the swap for Ubuntu, and the 4th must be the hidden image of the Windows Operating System (this is an OEM computer).

I wouldn't mind blowing away Windows.  I have my important files in a backup.  I do want to keep the image of the OEM.

How can I partition when I can't login??

Just FYI:  I don't have a writeable CD-ROM.

Thanks.

---

### Post by moose53 on 2008-02-13
Well, latest and greatest:

I had to blow away the Windows ME installation because I obviously did not have enough room to run both operating systems simultaneously.  I was finally able to see that the sd3 was 100% used.

I'm in the process now of getting back my files.

So, I guess this is resolved.  I'm now officially an Ubuntu user :guitar:

Thanks.

Barb

---

