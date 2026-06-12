---
title: "Backup files from ntfs onto linux"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by MNOB07 on 2006-05-17
I have to reinstall Windows, the Windows drive's boot information or something got screwed up due to Partition Tragic. I am hoping to see what I can recover using Linux and so I have Ubuntu installed on a seperate harddrive right now.

I want to copy the files onto Ubuntu's hard drive, and then transfer them back to the Windows drive  (if Ubuntu does not support writing to NTFS then that's ok as long as Windows can read the linux drive... which I'd assume is the default filesystem when installing Ubuntu whatever that is?

EDIT: I meant to ask for a step by step or something because I don't even know how to mount the hard drive

---

### Post by Sef on 2006-05-17
GNU/Linux can read NTFS, but cannot write to it.  Instead try this rescue disc:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

It has captive, which can read and write to and from NTFS.

---

### Post by ZiLOG_Z80 on 2006-05-17
to read the windows ntfs partition in ubuntu, follow this [guide]("http://ubuntuguide.org/#mountunmountntfs")

As for reading the files from the linux partition, windows cant read the file system used by ubuntu which is ext3 by default. I have seen utilities for doing it though never tried any. [this is one]("http://www.fs-driver.org/") you could try, but it may just be easier to burn them off to dvd or something

---

### Post by jpkotta on 2006-05-17
I have used ext2ifs to read ext2/3 from Windows (read only).  It worked well, and is free.

[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

To mount an NTFS partition, just look here: [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

Also, look at the ntfsclone utility here (I haven't tried it): [https://wiki.ubuntu.com/NTFSReadWrite](https://wiki.ubuntu.com/NTFSReadWrite)

---

### Post by catlett on 2006-05-17
```
I have used ext2ifs to read ext2/3 from Windows (read only)
```
You can read and write with est2fs. It is very simple to install and use. Just download and run it. Once you run the install program, in your windows control panel will be an icon for the ext2fs driver (it's easiest to find buy switching the control panel to "classic view")
When you hit on the icon and the application opens you will see your hard drive much like you see it in Partition Magic. The Ubuntu ext3 partitions won't have a drive letter. But they will have a drop down box. When you hit on the box it will drop down with a list of all available drive letters. You choose a letter and close the application. When you go to "my computer" the Ubuntu partition will be listed next to your C partition with it's own icon.(there will be 2 Ubuntu ext3 partitions. you only need the larger one. the "swap" will be available to you but there is nothing on it because it is used as Ubuntu's version of the swap file) 
Hit on it like you would your windows C icon and all the folders of Ubuntu will be there. You can read,write,delete and anything else you want because you will be using it as an administrator in windows. Good luck with your recovery.

---

### Post by RRS on 2006-05-17
Does your Ubuntu drive have enough room for another partition? If so use the installation CD to create a Fat32 in addition to the existing Ubuntu partition.

Windows and Linux can both read and write to Fat32 so you'll be able to copy your Windows files from Ubuntu andf then copy them back from Windows after reinstalling, or simply leave them there for future access when needed.

[Heres]("http://easylinux.info/wiki/Ubuntu#Windows") a  guide to mounting your partitions and [this site]("http://users.bigpond.net.au/hermanzone/index.htm") has similar directions and several other usefull tips.

I'm currently in the middle of a similar "salvage" operation myself, just haven't found a good reason to spend time finishing and "getting Windows back".

Hope this helps.

---

### Post by aysiu on 2006-05-17
I'm with ZiLOG_Z80 on this.

Mount Windows and copy the files
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Then use Windows to copy the files back
[http://www.fs-driver.org](http://www.fs-driver.org)

---

