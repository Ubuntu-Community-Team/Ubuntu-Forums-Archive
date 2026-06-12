---
title: "Ubuntu not seeing all HDDs"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ben0r on 2007-04-27
Howdy,

When I was installing ubuntu, it asked me which hdd I would like to setup the filesystem on, and in that list, it saw every harddrive that I had.

Now that the OS is going, i do not see 1 of my sata hdds.  

Background: I had windows on a 2x160gb raid 0.  I deleted the raid and now running them as single drives (sata connections straight from the mobo).  I installed ubuntu on the first of the 2 drives.  Ubuntu sees the first 160gb drive, but not the second now that I'm in the os

Do I need to get some equivalent to "Disk Storage Management" that windows had, so I can properly format the second drive?  Cause it probably still has 1/2 of all my files from my windows install (since it was on a raid...that actually had 2 partitions-- 8gigs for windows and the rest for storage)

thanks

---

### Post by lamalex on 2007-04-27
sudo fdisk -l

then mount the drive that's not listed, probably /dev/sdb
mkdir /media/drivename
sudo mount /dev/sdb /media/drivename

should do the trick. or if you wanted to emulate your raid 0 like in windows you could set up LVM (alternate install cd) that would tell it to lump both drives into one and then cut it up into partitions if you want, or just leave it as one /root partition.

---

### Post by ben0r on 2007-04-28
Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

ben@ben0r:~$ mkdir /media/mr160
mkdir: cannot create directory `/media/mr160': Permission denied
ben@ben0r:~$ sudo mkdir /media/mr160
ben@ben0r:~$ sudo mount /dev/sdb /media/mr160
mount: you must specify the filesystem type
ben@ben0r:~$

---

### Post by houstonbofh on 2007-04-28
Open synaptic, and install Gparted.  run it and tell us what you see. (A screen shot is fine) It sounds like disk 2 is corrupt, and Gparted can reformat it if that is what you want.

---

### Post by ben0r on 2007-04-28
[IMG]http://www.patsargent.com/gparted.png[/IMG]

ok I guess I'm just a huge newb.  I cant figure out how to format it, or what to do from here.  I think I created the partition table?  Do i need another swap, or is that just for the OS

and don't i have to mount the drive, then add it to my startup commands?  I hate that I used windows for so many years...i'm so lost :(

---

### Post by ben0r on 2007-04-28
guh

---

### Post by mgmiller on 2007-04-28
One problem is that you were using raid 0.  There is no redundancy and any files stored on it are lost when you break the raid.  It is essentially just a big empty drive now.  You will probably have to delete and recreate the partition information.  Gparted can do that.  For Linux, create an ext3 file system.  There is another utility called pysdm that will help you get it mounted.  After pysdm is installed, look in System>Administration>Storage Device Manager.  It will let you set up mount points, etc. graphically.

---

### Post by houstonbofh on 2007-04-29
It is there.  I would recreate it as a primary partition.  Where you mount it is the next question.

---

