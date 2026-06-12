---
title: "Unable to mount second CD ROM"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by cchase on 2007-08-24
I know that this post has been asked like 6 times already but I just don't understand Geekaneeze very well yet and I am haveing a very hard time understanding what to do.  I am running Ubuntu Dapper Drake.  I have two CD ROM drives.  In windows, drive "D" was the ATAPI, Drive "E" was LITE-ON.  The LITE-ON is my CD-RW drive.

When looking in Places/Computer I see both drives as CD-ROM Drive and CD-RW drive.  When I place a CD in the CD-ROM drive the disk pops up on my desktop and I am able to access it fine.  When I put a disk in the CD-RW drive it spins up but nothing happens.  If I double click the CD-RW drive it gives me the error 
"Unable to mount selected volume

mount: no medium found

mount: no medium found

error: could not execute pmount"

I typed in a couple of the commands asked for in previous posts and tis is what I get (if it helps any):
> cchase@Office:~$** dmesg | grep CD**
[17179575.896000] hdc: ATAPI CDROM, ATAPI CD/DVD-ROM drive
[17179576.344000] hdd: LITE-ON LTR-12101B, ATAPI CD/DVD-ROM drive
[17179576.472000] hdc: ATAPI 44X CD-ROM drive, 128kB Cache, UDMA(33)
[17179576.472000] Uniform CD-ROM driver Revision: 3.20
[17179576.472000] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
cchase@Office:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0   

I very much appreciate any help.

---

### Post by nonewmsgs on 2007-08-24
in a terminal try 
sudo mount /dev/hdd /media/cdrom1

---

