---
title: "New Hard Disk"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by z3r0-c0d3r on 2006-02-26
I got a new 120gb SATA hard disk and a new motherboard and plugged it in with my existing IDE hardrive but ubuntu doesn't detect the new hardrive!

How can i get it to detect the hard drive?

Everything else works fine except i can't find the harddrive, the only hardware i changed was the motherboard and added a new hardrive

Does anybody know how to get this working?

---

### Post by GreyFox503 on 2006-02-26
Well, if it's the only serial ATA device on the system and you don't have any USB flash drives plugged in, then it's probably been labeled /dev/sda.  I would try running a partitioning program like fdisk or gparted to see if it sees the disc.  Gparted is available in the repositories, and it has a nice GUI.

---

### Post by Sutekh on 2006-02-26
[QUOTE=z3r0-c0d3r]
How can i get it to detect the hard drive?
[/QUOTE]
Well let's be sure that its not detected first.

Have you tried looking in the System -> Administration -> Disks menu?

---

### Post by procras on 2006-02-26
Did you install this as with a SATA cable or an IDE cable.
Some disks can use either and there may be some jumpers to set on the disk. Check the documentation that came with your disk.

Did you forget to plug in the power connection to the drive? SATA drives use a differnt non MOLEX connector to the drive and if you have an old power supply then you will have to get an adaptor to connect the MOLEX connector to the edge power connector for the drive. No power means the disk with not work.

What SATA chipset is on your board? Some boards even have two sets and one may be better supported than the other, they may be different colours etc.

The SATA chipset may have been disabled in the BIOS for some reason, check that it is not.

Was the disk recognised on the boot up sequence? Look for the messages following boot up with dmesg and search for SATA and a disk, you may see which device it is connected to, /dev/sda is a good choice if nothing else like a USB pen or zip drive is connected.

If it is connected then you can then;
* partition it with fdisk
* create a filesystem on it with mke2fs
* Make a mount point for it on your root partition eg. /mnt/driveb or whatever
* create an entry in /etc/fstab so that the disk is automatically mounted at boot if that is what you want

---

### Post by GreyFox503 on 2006-02-26
procras:  Wow, that covers just about everything.  I don't have SATA in my system, so I've never had to deal with all that stuff.

---

