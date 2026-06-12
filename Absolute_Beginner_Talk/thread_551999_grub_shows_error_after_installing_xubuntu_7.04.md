---
title: "grub shows error after installing xubuntu 7.04"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by arai on 2007-09-15
i downloaded xubuntu 7.04 and installed it. after install, reboot grub shows an error. what do i do now?

---

### Post by st33med on 2007-09-15
Could you at least type what appears on screen?

---

### Post by alienexplorers on 2007-09-15
What error is it that grub or whatever display's.

---

### Post by arai on 2007-09-15
```
sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5227    41985846    7  HPFS/NTFS
/dev/hda2            5228        5783     4466070    c  W95 FAT32 (LBA)
/dev/hda3            5784        8843    24579450    f  W95 Ext'd (LBA)
/dev/hda4            8844        9729     7116795    b  W95 FAT32
/dev/hda5            5784        6038     2048256    b  W95 FAT32
/dev/hda6            8334        8588     2048256   82  Linux swap / Solaris
/dev/hda7            6039        8045    16121196   83  Linux
/dev/hda8            8046        8316     2176776   83  Linux
/dev/hda9            8317        8333      136521   82  Linux swap / Solaris
/dev/hda10  *        8589        8824     1895638+  83  Linux
/dev/hda11           8825        8843      152586   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by alienexplorers on 2007-09-15
So what is the error.  I see your fdisk -l list.  I don't see an error.

---

### Post by arai on 2007-09-15
grub loading

error 15

---

### Post by Duck2006 on 2007-09-15
Have you tryed reinstalling grub?

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by arai on 2007-09-15
also xubuntu 7.04  live cd is not booting. i dono why

grub is creating lot of problems for me. is there any alternative to grub which i can just download, install and use?

> Have you tryed reinstalling grub?

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

yes, grub shows nothing.

---

### Post by dwhitney67 on 2007-09-15
> **arai said:**
> grub loading

error 15

That means a critical file used by grub was not found.  It could be the kernel, it could be the device.map, or menu.lst.

I have never done a dual-boot installation, so I can't even begin to comment how to setup your system.  Was it working before?  Or are you installing a fresh Ubuntu system?

Why do you have so many swap partitions?  Only one is required.  If you have multiple Linux distros on your system, have each use the same swap space.

Upon closer inspection of your fdisk output, I cannot begin to imagine why you have multiple partitions intersecting each other (i.e a Linux partition intersecting with a Win partition, a swap with a Win partition, etc.).

Looks to me that you need to start over with your approach to installing Ubuntu.

---

### Post by uglykigjoe on 2007-09-15
> **arai said:**
> also xubuntu 7.04  live cd is not booting. i dono why.

did you set your boot sequence to start boot from CD/DVD?
i can suggest you this link-->

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by arai on 2007-09-15
winxp is already installed. worked properly for months.

xubuntu 7.04 installed through desktop cd yesterday.

now system is not booting.

---

### Post by uglykigjoe on 2007-09-15
So i hope this helps: 


"I installed GRUB to MBR with a Gnu/Linux distro (dual boot), and Windows no longer boots."

1) I just want to boot Windows for now, I'll fix it later,

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Boot Windows

This will boot Windows for now for you and you can verify that Windows is still okay and able to be booted. You can access all your data and get any urgent work done. You can fix the problem more permanently later on when you have time or you are in a better mood.

2) I  want my MBR pointing to Windows  bootloader again  - right now!

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Fix Boot of Windows



I installed Windows on a first hard disk but I unplugged it and plugged it in as a non-first hard disk. Now I want to boot it.

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Boot and Tools
   4. Boot Master Boot Record (MBR)


Original Link: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

---

### Post by alienexplorers on 2007-09-16
You could also follow the directions in my signature line and reinstall grub from live-cd.

---

### Post by arai on 2007-09-16
can anyone tell me why  xubuntu 7.04 desktop cd is not booting ?

---

### Post by dwhitney67 on 2007-09-16
Not without further information from you (i.e. what are the errors, issues, etc).  :)

---

### Post by arai on 2007-09-16
> So i hope this helps: 


"I installed GRUB to MBR with a Gnu/Linux distro (dual boot), and Windows no longer boots."

1) I just want to boot Windows for now, I'll fix it later,

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Boot Windows

This will boot Windows for now for you and you can verify that Windows is still okay and able to be booted. You can access all your data and get any urgent work done. You can fix the problem more permanently later on when you have time or you are in a better mood.

2) I  want my MBR pointing to Windows  bootloader again  - right now!

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Fix Boot of Windows



I installed Windows on a first hard disk but I unplugged it and plugged it in as a non-first hard disk. Now I want to boot it.

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Boot and Tools
   4. Boot Master Boot Record (MBR)


Original Link: [http://users.bigpond.net.au/hermanzo...l#boot_windows]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows")

How do you expect me to use a super grub disc. i simply can't login to win/lin. i use live ubuntu cd to write this. i have only one cd r/w drive.

---

### Post by dwhitney67 on 2007-09-16
Do you not have access to another PC?  Perhaps a friend's PC, or one at the office/school?

---

### Post by arai on 2007-09-16
i am tryinig to use sgd in a flash drive. i will update if it workd.

---

### Post by arai on 2007-09-16
thanks 2 all who replied this thread. i used ubuntu 6.10 edgy to boot and install ubuntu. the xubuntu cd failed to boot, may be it doesn't support my old monitor.

---

### Post by arai on 2007-09-16
with great difficulty i installed xubuntu 7.04

can anyone tell me how to increase or decrease the sound in xubuntu 7.04 ?

---

