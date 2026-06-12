---
title: "USB stick problem - plus CUPS vs LPR question"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by the-edmeister on 2008-03-07
I can't seem to find how to access a USB stick and its' contents on Ubuntu 7.10 or openSUSE 10.3. The USB port is working with my Epson 880 Inkjet printer.
Stick was loaded on W2K running FAT32, so I suppose the stick is FAT32 - not NTFS. There is no desktop or taskbar icon when the stick is plugged in, and I can't find the stick through Nautilus - in either OS.


As far as the Printer question - I am running a Brother HL-2070-N Laser Jet, attached to my LAN with a Network cable. I am printing directly to the printer over the network - peer to peer - no central server involved.
Brother - Linux Driver homepage  - [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)
Which is the best for me to use in Linux - the LPR driver or the CUPS driver?
Am I gonna need a different set of drivers for Ubuntu (the Debian drivers) and openSUSE (the RedHat drivers)?


Ed

---

### Post by ajgreeny on 2008-03-07
Can't help with the printer, but for the usb stick, plug it in then in terminal ```
sudo fdisk -l
``` to see what the disk is listed as.  Also worth seeing the output of ```
cat /etc/fstab
``` to see if that is at fault in some way.

---

### Post by Ferio on 2008-03-07
I seem to get the same problem: sometimes my stick gets mounted, and sometimes it doesn't; fdisk says my stick hasn't got a valid partition table, but I've used it to move things from a PC to another...

---

### Post by the-edmeister on 2008-03-08
In Ubuntu:
```
eddie@ASUS:~$ sudo fdisk  -l

Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6385650

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         243     1951866   83  Linux
/dev/hda2             244        2491    18057060    5  Extended
/dev/hda5             244         972     5855661   83  Linux
/dev/hda6             973        1033      489951   82  Linux swap / Solaris
/dev/hda7            1034        1834     6434001   83  Linux
/dev/hda8            1835        1994     1285168+  82  Linux swap / Solaris
/dev/hda9            1995        2491     3992121   83  Linux

Disk /dev/hdb: 20.4 GB, 20490559488 bytes
16 heads, 63 sectors/track, 39703 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

Disk /dev/hdb doesn't contain a valid partition table

```
I don't see the stick listed. /dev/hdb is the DVD drive.

```
eddie@ASUS:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=f844b3a9-5d45-4fea-a9d6-e223c4899ba5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=b315cd6f-f67b-4567-ba11-48c8f85c19df /home           ext3    defaults        0       2
# /dev/hda6
UUID=9a0fef91-a768-4941-958b-1e185e1951c8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Ed

---

### Post by the-edmeister on 2008-03-08
I couldn't find the terminal in OpenSUSE, but I opened it in FailSafe.
```
 sudo fdisk -l 
``` command not found

```
 cat /etc/fstab
```
- part 7
- part 9
- part 6
- part 8
no cdrom0
no stck

The AMI boot screen recognizes the stick as a Kingston Traveler as USB Device #01, so the hardware check part of BIOS "see's" the stick.

No light on the stick when I plug it in or when I re-boot with it plugged in. Are their any diagnostic routines built into either OS, or on their LiveCD?

*Edit:* Just realized that memory sticks aren't formatted to FAT32, but rather FAT. Does Ubuntu.OpenSUSE read FAT?


Ed

---

### Post by ajgreeny on 2008-03-08
Not sure about the fat as opposed to fat32 (or fat16), but if there are no files that you need on the USB flash drive, I suggest you try to reformat it in ubuntu using gparted.  Install it if needed, or use the liveCD which has it already and format the drive, assuming it's found by gparted, as fat32.  It may be that the format is corrupted in some way, or even that you have used it in a windows machine and not removed it properly, which can upset things some times.  In future make sure you eject the drive properly in windows as well as ubuntu before you unplug it to save the possibility of this happening again.

---

### Post by the-edmeister on 2008-03-08
The stick has Firefox Profiles I am trying to transfer from my Windows box. I always "Eject" the stick thru the OS, and I can still read this stick in my WinXP laptop along with the W2K box the files came from, so I doubt if corruption is the issue here.

I am wondering if the LiveCD installation didn't install something, the OS just doesn't see the stick - no light and no listing when running - sudo fdisk -l 

When I get home tonight I see what I can come with thru GParted.


Ed

---

### Post by ajgreeny on 2008-03-09
If you can still get the firefox profiles from windows after reformatting, in either windows or ubuntu, it would be worth trying that.  It doesn't take very long to do it, after all.

---

### Post by the-edmeister on 2008-03-10
I tried a different USB memory stick. This stick tries to connect - I see the LED flash once then flicker twice, but the LED doesn't stay lit. I don't see an icon for the stick and I still don't see the stick when I run cat /etc/fstab in the Terminal.

I couldn't do anything GParted, I couldn't format the memory stick. I would almost think this was a hardware issue, but my USB connected printer works.

Are there any CD-based tools that I can use to run a hardware check of this?


Ed

---

### Post by ajgreeny on 2008-03-10
Try 
```
sudo fdisk -l
``` again

---

### Post by the-edmeister on 2008-03-11
Ok. I finally got the USB stick to work by using the rear USB ports directly off the mobo.
```
lsusb
```
That terminal command started me thinking that I might have a hardware related problem, as I tested all the USB bus's one at a time. Voila, when I used the 4 rear ports a USB stick was recognized in all those ports but not in either of the 2 front case ports.
Now the question is why my printer works in either of the front ports but the USB stick isn't recognized in either of them?


Ed

---

