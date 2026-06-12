---
title: "absolute beginner"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by barrykgerdes on 2006-04-04
Hi
I am having a great deal of trouble getting started on ubuntu linux. I have been a DOS and Windows user for 23 years now but can't seem to get the basics of linux.

There are a number of things I need to know but the first ones are:-

1.  How to read and write to a floppy disk
2.  How to mount my Windows and DOS partitions for read and write so I can access
     my document files etc.
3.  How to erase files and folders that have been created in various places in error
     that are now owned by root and won't let me do anything but read.

These are all basic functions that have been easy to accomplish in DOS and Windows.

Barry

---

### Post by Zimmer on 2006-04-04
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Reading this should give you a better insight into the methods used for accessing files and admin functions that are deemed to be owned by ROOT.
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
may help you with mounting Windows partitions , but be aware that NTFS is read only..

the tuxfiles link in my signature is a good tutorial on file permissions (one that I actually understood!)
There are also a lot of existing threads with tips on accessing Windows partitions and Floppy disk access. The floppy is a drive that will need to be mounted.
A few tips here
[https://wiki.ubuntu.com/MakeFloppyDriveAvailableToEveryone](https://wiki.ubuntu.com/MakeFloppyDriveAvailableToEveryone)

---

### Post by Sef on 2006-04-04
> 1. How to read and write to a floppy disk

In Breezy, there is a bug that is fixed in Dapper.  The floppy doesn't automount.  There is a fix, but it doesn't always work.

---

