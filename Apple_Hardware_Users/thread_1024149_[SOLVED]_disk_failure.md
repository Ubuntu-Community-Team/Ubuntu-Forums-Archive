---
title: "[SOLVED] disk failure"
date: 2008-12-28
forum: Apple Hardware Users
---

### Post by vegetali on 2008-12-28
A friend of mine has an iBook G4, and she has serious problems with her hard drive (a toshiba, 35Gb). During normal usage, the OS crashed and the disk was found corrupted. She could recover the data by rebooting after the crash, but it seems the disk got serious damage. She tried to wipe the disk using the macos installation disk, but it failed. So I was trying to isolate the damaged blocks and create a functional partition on the disk by using linux. It is long time I have tried to convince my friend to switch to ubuntu, and I almost succeeded. Solving this issue could be the final push, that's why I am asking for help here.

I know Knoppix is usually a good live distro to deal with this kind of issues, but it seems there is no PowerPC version. By the end, I decided to go for an ubuntu desktop live CD (8.04.1) and try to solve the problem LIVE (ok, I also tried the server version but it did not boot because it is not live and could not install on the HD). During the boot (from the live CD), I receive some errors of the form

"Buffer I/0 error on device hda, logical block 12"

and once I also get this error that I do not understand

"IDE-PCMAC lost interrupt, DMA Status 8480"

It seems that the total number of damaged blocks is just 17 (and they are almost contiguous); if I am not wrong a block is 512bytes by default, so it is a negligible amount of space on the HD. 
After that, the boot is ok but no HD device is then detected by the system. Namely, Gparted does not find any disk, nor I can get any in /dev (there is just an empty 32kbyte /dev/hda1 and I do not know what it is). My idea was to run dd or badblock, and then doing some partitioning. But I do not know what to do in this case.

Any help would be much welcome, as I am not in the USA (you may guess that from my poor english) and replacing a mac hard drive is crazy expensive. Thanks.

---

### Post by arvevans on 2008-12-28
First, read this:
[http://www.linuxjournal.com/article/193]("http://www.linuxjournal.com/article/193")

It may help you understand what you are up against, and will suggest some Linux tools to use for further analysis and possible repair.

**_NOTE:_  The procedures listed here will cause loss of data stored on the hard drive.  If you have needed data stored there, you may need to attempt backing up that data on another drive before going further.**

When a hard disk crashes, there is usually some physical damage to the disk surface, and possibly to the head which was involved in that crash.  While you might be able to partition around a crashed platter, it would be difficult to do so.  Also, a disk crash usually leaves some debris floating around inside the disk housing, which has potential for causing a crash on other platters.  The best approach would probably be to purchase and install a replacement disk drive if you are sure that the existing disk has actually crashed.

It is possible that what you are seeing is corruption of data and/or synchronization tracks on the existing hard drive.  Depending on the drive and on it's age, you may be able to do a low-level format of the whole hard drive, including the boot track, and at least temporarily recover the drive.  This would involve running fdisk (or one of the fdisk-like programs) to remove all file systems, refresh the MBR sector ("fdisk /mbr"), write and sync the no file systems disk (usually involves a re-boot).  Then do the fdisk thing again to build new partitions.  Disk integrity tests will be run when defining the new partitions and should tell you if the disk has un-recoverable physical damage.  After doing the partition rebuild and re-sync you will need to do a regular format of those partition types which need to be formatted for a particular file system structure.  Once the disk partitions have been successfully re-formatted, you can use the Linux "fsck" program to check disk partition integrity.  From a terminal window do "man fsck" to see the available options for fsck.

Good luck.

---

### Post by vegetali on 2008-12-28
Thanks. It seems that the command debugfs described in the article may help. My main problem now is to let the system recognize the hard drive device. It did detect it during the boot (advising about errors on the disk), but when I get to the command line the device is not there anymore.

---

### Post by arvevans on 2008-12-29
Try "sudo lshw" to get a hardware listing.  That may show you enough information to help with manually mounting the hard drive.  If you can get it to mount, then you may be able to run the necessary diagnostics.

---

### Post by vegetali on 2009-01-04
thanks. By the end, the disk had a physical crash, and needed to be replaced. Thank you BTW.

---

