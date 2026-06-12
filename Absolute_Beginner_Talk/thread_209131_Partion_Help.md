---
title: "Partion Help"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by MOSFET_MOSFET on 2006-07-04
I have decied to install Linux, and I have only 1 final question before I do.


If i use the auto partion ....then its says it will shrink my windows partion...and make the Linux one from the free space. How big will this make the windows partion ? Because I still need to use windows for certain appiclations. 


Also, can I transfer data between partions ? windows is on NTFS at the moment.

Thanks To All Who Post

---

### Post by Jagot on 2006-07-04
If I were you I'd resize the Windows partition to however big you want it - not rely on the installer.

If your Windows partition is currently on NTFS, Linux can read from the partition but not write to it.  If you want to share files between the two partitions without using external media then you would need to set up a FAT32 partition.

---

### Post by aysiu on 2006-07-04
You may want to read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by MOSFET_MOSFET on 2006-07-04
[QUOTE=Jagot]If I were you I'd resize the Windows partition to however big you want it - not rely on the installer.

If your Windows partition is currently on NTFS, Linux can read from the partition but not write to it.  If you want to share files between the two partitions without using external media then you would need to set up a FAT32 partition.[/QUOTE]
 
That sounds a little trcikey....know any good links ?

---

### Post by Average_Joe on 2006-07-04
MOSFET --

Sounds like your situation is exactly the same as mine at the moment I decided to install Ubuntu alongside Windows XP.

What I did (which was successful) was use GParted (bootable CD) to make the Windows NTFS partition smaller.  That way, I could choose the size of my NTFS partition before using Ubuntu LiveCD.

GParted is very fast and easy to use.  If you want to use GParted from a GParted LiveCD, just click here:
(burn the .iso file from 26 June)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by catlett on 2006-07-04
The auto partitioner takes around 12gb, give or take a few. It's been a while. You will be able to read ntfs files from linux but not write to an ntfs partition (there are some ntfs linux drivers but since the source code is closed they are reversed engineered and are not 100% reliable. They are "use at your own risk".)
There is a windows driver that will allow you to read and write to ext3 partitions (that is the type ubuntu will be on) This way you can copy over whatever you want from windows to linux and if you want something you got while in linux, just save it and get it in windows with the ext3 driver. Then if you want it on your ntfs partition let windows copy it from the ext3 to the ntfs partition. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

