---
title: "CD ROM not detected"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by JBS on 2007-08-09
I took an old computer, put in a hard drive and 2 CD ROMs and tried to install Xubuntu.  I kept running into the same error and searched until I found the solutuion [here]("http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html").
I had to disconnect one of my CD ROMs, so I did.  They're both on the secondary IDE cable and the one I disconnected, but didn't realize till later, was the master, but, the slave still worked anyway and I was able to install Xubuntu.
Afterwards I followed the rest of the instructions in the link and restarted the computer.  I can access the hard drive fine, and I have a flash drive that's instantly mounted when I plug it in, but nothing with any of the CD ROMs.  I've tried putting CD's in them, but nothing happens.
I've searched a lot for the answer, but still being so new to Linux, I'm having great difficulty.  In the other threads about CD ROMs not mounting people are told to dmesg | grep CD and cat /etc/fstab so I did that, and here are the results:
dmesg | grep CD
```
[   36.569778] hdc: Pioneer CD-ROM ATAPI Model DR-A24X 0104, ATAPI CD/DVD-ROM drive
[   37.353399] hdd: ATAPI CDROM, ATAPI CD/DVD-ROM drive
[   97.508124] hdc: ATAPI 20X CD-ROM drive, 128kB Cache, DMA
[   97.508142] Uniform CD-ROM driver Revision: 3.20
[  457.360084] hdd: ATAPI 48X CD-ROM drive, 128kB Cache, DMA

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d98b88a1-3e51-4cac-930a-3b5c6065fbd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=79a0345f-d4e8-4f02-891c-1ae8d67bc62a none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by JBS on 2007-08-09
Nothing funny about either output?

---

### Post by deadgobby on 2007-08-09
THe roms are there. Have you tried this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

---

### Post by JBS on 2007-08-09
sudo mount /media/cdrom0/ -o unhide
gets me
Special device /dev/hdd does not exist

And, just because, I tried sudo mount /media/cdrom1/ -o unhide
which got me
Can't find /media/cdrom1/in/etc/fstab or /etc/mtab

> **deadgobby said:**
> THe roms are there. Have you tried this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

---

### Post by JBS on 2007-08-09
Wow, I'm surprised that with the info I've offered that nobody knows what to do.

---

### Post by Wolfie Lee on 2007-09-30
> **JBS said:**
> Wow, I'm surprised that with the info I've offered that nobody knows what to do.

Sorry, I'm not going to be any help either. It sounds like you have the exact same problem I'm having, No matter if You try to mount from desktop or console, your device isn't being detected, so you can't mount what the OS can't see. I have a 16xDVD burner, and a 48xCDburner, but I can only use the DVD, and would like to use cd for speed, sometimes, or have two disks in and mounted at same time, but can't. I have DVD as secondary master IDE and CD as slave. I will be following this thread, but the fix is not as simple as console mount vs. desktop mount....maybe that will help someone take a closer look at the problem from that perspective..........:-?

---

