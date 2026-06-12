---
title: "How do I format and install a hard drive in Ubuntu?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by tmcarson1 on 2007-08-01
I have a 30GB Maxtor internal hard drive physically installed in my system, yet it does not show up in Ubuntu (this is the old XP drive).  

I would like to reformat this entire drive for storage in Ubuntu, how can I get Ubuntu to recognize it so I can reformat it?

Thanks!

---

### Post by Happy_Man on 2007-08-01
Is it internal or external?

---

### Post by tmcarson1 on 2007-08-01
Internal (ATA I think) just a normal hard drive you could buy at any circuit city.

---

### Post by apswartz on 2007-08-01
If it is recognized by your computer's BIOS then you should be able to use fdisk to create partitions.

---

### Post by sep1318 on 2007-08-01
I'm not exactly sure where you're coming from with this, but I'll try my hand. You need to mount the drive, so that Ubuntu knows where it is. If you have a command line open, type ```
ls /dev | grep da
``` and that should give you a list of a bunch of sda# or hda#, depending on what format ubuntu thinks your connections are. then ```
mount -l
``` to see what's already mounted. The drive that isn't mounted should be apparent by comparing the lists. ```
sudo mount /dev/(h/s)daXX /media/diskWhatever
``` will hopefully mount the disk so that you can access it. Then you can reformat it using gparted or w/e, preferrably to something like ext3. Does that help?

---

### Post by digitalslavery on 2007-08-01
sorry to butt in on this thread, but I am having a similar issue, I followed your steps to show the drives and my list is :
hda
ptyda
ttyda


and when i try to format using 
sudo fdisk /dev/hda

I get this error: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

and then using -w I get unable to write to /dev/hda

This is the second hard drive I tried and its the same error for both drives. I just tested a windows install on the drive and had no issues.

---

### Post by bobpur on 2007-08-01
Go to [www.distrowatch.com](www.distrowatch.com) and download "Gparted" and burn it to a cd. This is a "live" cd so there is nothing to install.
I like using gparted to format harddrives rather than using the version found in OS cd's.
BTW, Parallel ATA drives will show up as "hda", "hdb", etc. Serial ATA drives will show up as "sda", "sdb", etc.
Also, for PATA drives, jumper settings are important as well as placement on the cable.
The cable has three connecters. The middle one is the slave connecter and is offset from the center of the cable. Drives connected here should be set to "SL" (Slave) or "CS" (Cable Select) The end connecter closest to the slave connecter is the "Master" connecter. Drives using this connecter should be jumpered to "MA" (Master) or "CS"(Cable Select). The connecter furtherest from the slave connecter is the end that plugs into the motherboard.
Using drives from two different manufacturers will sometimes require you to "play" with your jumper settings to get the "master" and "slave" settings correct.  Example: Master & Cable Select or both drives set to Cable Select. Setting both drives jumpers to "CS" lets the placement of the drive on the cable determine its function.
Improper jumper settings and/or cable position can cause a drive not to be recognized by the OS.
                                        Good Luck

---

