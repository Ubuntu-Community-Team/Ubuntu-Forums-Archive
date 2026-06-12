---
title: "Using an Ipod 30Gb"
date: 2014-03-25
forum: Apple Hardware Users
---

### Post by aneblanc on 2014-03-25
I inherited an old ipod 30gb. I can listen to the music what is on it but I can't delete or upload anything. It's read only. 
How can I change that?

I probably would like to format it or at least delete the files on it and load my own MP3 files and pictures. 
What program can I use? 
Or can I keep the apple programs that make the thing work as an ipod? 
Is this an option with Ubuntu?

---

### Post by tgalati4 on 2014-03-25
You can install rockbox or jsymphonics or you can fsck the drive to make sure it is "clean" so it will mount properly.  If originally formatted on a Mac, you need to turn off journaling on the drive (turning HFS+ into an HFS drive) using the Disk Utility in OS X.  If FAT32 formated, then just perform an *fsck* to check the drive.

---

### Post by aneblanc on 2014-03-25
I have used the disk utility program and ran the Check filesystem. It says that the file system is not clean.

The partition type is HFS+

Can I use the format option to get rid of the read only setting? Is it safe to do so?

---

### Post by aneblanc on 2014-03-25
> **tgalati4 said:**
> If originally formatted on a Mac, you need to turn off journaling on the drive (turning HFS+ into an HFS drive) using the Disk Utility in OS X. 

How do you turn off the journaling using the disk utility in Ubuntu?

---

### Post by aneblanc on 2014-03-25
Oh I see I need a mac to perform this...

---

### Post by tgalati4 on 2014-03-25
It's safer to use the utility on a Mac, but there are some utilities in linux that will do it.

hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes
hfsprogs - mkfs and fsck for HFS and HFS+ file systems

---

### Post by aneblanc on 2014-03-26
I downloaded the programs but I really don't know what I am doing. It seems that I have to use them from a terminal and I haven't a clue about the syntax.

Isn't it easier to just format the filesystem partition with the disk utility provided with Ubuntu 12.04 and start with a new format? 
Or am I going to ruin something?

---

### Post by aneblanc on 2014-03-26
I found this post [http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

and did what it says at the end of the post:

Plugin the external HDD 

Notice that Ubuntu mounts it automatically but it is read-only

Unmount the drive (I do this simply by clicking on the eject button in the file explorer).

$ sudo apt-get install hfsprogs

$ sudo fsck.hfsplus /dev/sdb3 -f

/dev/sdb3
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking Extended Attributes file.
** Checking volume bitmap.
** Checking volume information.
** The volume XXXXXXXX appears to be OK.

The volume is still read-only.

What should I do next?

---

### Post by aneblanc on 2014-03-26
I found this:

[http://serverfault.com/questions/25251/disable-journaling-of-hfsplus-partition-in-systems-other-than-osx](http://serverfault.com/questions/25251/disable-journaling-of-hfsplus-partition-in-systems-other-than-osx)

*It seems the only 100% reliable way is to disable journalling in OSX, hfsplus-tools doesn't have the ability to disable it without reformatting.*

---

### Post by aneblanc on 2014-03-26
This

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

*HFS+ is the files system used on many Apple Macintosh computers by Mac OS. You can mount this filesystem in Ubuntu with read only access by default. If you need read/write access then you have to disable journaling with OS X before you can continue.*

seems to confirm the previous suspicion that it is not possible to disable the journaling under Ubuntu.

---

### Post by tgalati4 on 2014-03-26
Yes, I seem to remember that restriction.  So you can reformat to HFS under linux, but you wipe out the data.  If you use the Mac then you can simply turn off journaling using Disk Utility.  You will have to search for the utility to do it correctly.

[http://julipedia.meroh.net/2007/04/how-to-disable-journaling-on-hfs-volume.html](http://julipedia.meroh.net/2007/04/how-to-disable-journaling-on-hfs-volume.html)

[http://www.neowin.net/forum/topic/1081985-how-can-i-disable-journaling-on-an-external-drive/](http://www.neowin.net/forum/topic/1081985-how-can-i-disable-journaling-on-an-external-drive/)

[https://discussions.apple.com/message/16489755](https://discussions.apple.com/message/16489755)

---

### Post by aneblanc on 2014-03-26
Also 

[http://en.wikipedia.org/wiki/HFS_Plus](http://en.wikipedia.org/wiki/HFS_Plus) says:

*Under Linux's current HFS+ driver, journaling must be disabled in order to write data safely to an HFS+ partition; journaling can be disabled under OS X,[18][19] provided the partition isn't being used by Apple's Time Machine software. An HFS+ partition with journaling enabled may be forcibly mounted with write-access under Linux, but this is unsupported and unwise.*

---

### Post by aneblanc on 2014-03-26
> **tgalati4 said:**
> So you can reformat to HFS under linux, but you wipe out the data.  If you use the Mac then you can simply turn off journaling using Disk Utility.  You will have to search for the utility to do it correctly.


I cannot reformat to HFS under Ubuntu with the Disk Utility program but I can reformat to FAT or Ext4 or NTFS. I don't care about the data. Which format would you advise? (I don't have access to a mac and we have a snow storm right now!)

---

### Post by tgalati4 on 2014-03-26
I was referring to the Mac's Disk Utility program.  gparted with be able to wipe the drive and format it to FAT32.

---

