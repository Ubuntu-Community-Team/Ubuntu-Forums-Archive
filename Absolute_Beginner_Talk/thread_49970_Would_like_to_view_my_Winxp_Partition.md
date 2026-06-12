---
title: "Would like to view my Winxp Partition"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by Clafferty2 on 2005-07-18
Hello,

        I am a complete NOOB! So flame away if you must. I know next to nothing about Linux. But, I have succesfully installed Ubuntu along side my WinXP, so I have a dual boot system on a Presario 900 Laptop. I first downloaded the Live CD version of Ubuntu and was able to see my WinXP partion and was able to access it. After installing it along side WinXP I don't see it at all, and cannot find it. So, my question is: How do I enable my system so that I can see my hda1 partion and have read/write capabilities (please speak in Noob)? The hda1 partition is a NTFS and was origonally in Fat32<I still had the same problem with that as well, that's why I changed it to NTFS. Any and all help is greatly appriciated......

---

### Post by damonw5 on 2005-07-18
[QUOTE=Clafferty2]Hello,

        I am a complete NOOB! So flame away if you must. I know next to nothing about Linux. But, I have succesfully installed Ubuntu along side my WinXP, so I have a dual boot system on a Presario 900 Laptop. I first downloaded the Live CD version of Ubuntu and was able to see my WinXP partion and was able to access it. After installing it along side WinXP I don't see it at all, and cannot find it. So, my question is: How do I enable my system so that I can see my hda1 partion and have read/write capabilities (please speak in Noob)? The hda1 partition is a NTFS and was origonally in Fat32<I still had the same problem with that as well, that's why I changed it to NTFS. Any and all help is greatly appriciated......[/QUOTE]
 Go to "Disks" under the System menu (can't remember which sub-menu, sorry, but there are only 2 :) ) You should be able to see your Windows partition from there. What do you see there? Can you "mount" and "browse" it? Give us the details so we can help you better.

Sorry, you won't find lots of flaming of newbies here :)

---

### Post by Kyral on 2005-07-18
And writing to NTFS just doesn't work. Ignore what you hear about "captive NTFS", its just a fast way to corrupt you partition

---

### Post by damonw5 on 2005-07-18
[QUOTE=Kyral]And writing to NTFS just doesn't work. Ignore what you hear about "captive NTFS", its just a fast way to corrupt you partition[/QUOTE]
 Like Kyral says, you can read from an NTFS Windows partition all you want, but don't change anything on it or write anything new. If you can, you may want to convert it back to fat32 which has much better Linux compatibility.

---

### Post by Clafferty2 on 2005-07-18
I don't see the "Disks" area under either of the submenu's. There is Preferences and Administration, but it is not either, or I am blind???

---

### Post by Lord Illidan on 2005-07-18
You cannot write to your NTFS partition or edit files. That's definite. It will result in a corrupted registry and a hell of other problems. However you can always read the files, copy them to your Linux partition and edit them there.
Now, how to do it.. It is in the ubuntu guide, check it out...
[www.ubuntuguide.org](www.ubuntuguide.org)

Don't be ashamed if you are a newbie, we all were in the beginning...even Linus Torvalds... :smile:

EDIT : here is the direct link..

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by Clafferty2 on 2005-07-18
I am going to convert it back to Fat32 then try it again. Here is another question.... Does it matter if the linux partition Hda2 is Ntfs? Do I need to change that as well?

---

### Post by Clafferty2 on 2005-07-18
See, told you I was a NOOB. I should have looked there first.Thank you for the direction. If I have any problems I will post them in here.

---

### Post by tuba_smalls on 2006-06-11
Sorry to dredge up this thread, but I'm having a similiar problem.   I started using the Ubuntu LiveCD for 5 or 6 days and was able to mount my 300 gig hard drive with no issues.  The only odd thing was that I had to mount /dev/hdb5, and I am certain I had only one partition on the disk.

Once I install Ubuntu, and try to mount the 300 gig hard drive I start having problems.  In /dev/ there is only an hdb (no hdb# for the partitions on hdb), so i attempt to mount /dev/hdb and it seems to work.  I get no errors from the mount command.  When I try to access the directory I mounted to there is nothing in there.  I've done an hdparm on the disk and here is the result:

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 36483/255/63, sectors = 586114704, start = 0

================

I also did a listing of the partition table using fdisk and here is that result:


sudo fdisk -l /dev/hdb

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

===================

This output is very scary because I've never even used Novell Netware.  Several people have said use Ubuntu's Disk Manager (System -> Administration -> Disks) to check out the disk, but when I run it seems to hang indefinitely (entire window is ghosted and mouse has the busy icon).  

Finally I attempted to use gpart to guess the partition layout, but I immediately get this error:

sudo gpart -d /dev/hdb

*** Fatal error: dev(/dev/hdb): seek failure.

I also get the same error if I run gpart on hda (the disk and partition I am currently working on) so maybe I'm using gpart incorrectly.  Any help would be greatly appreciated.

Here is a history of the disk:
Only used as a storage disk, has no operating system on it.
When it was formatted and partitioned I created a single partition.
The file system is NTFS.

Thanks.

---

