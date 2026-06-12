---
title: "hard drive problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by tuki on 2007-05-05
im trying to plug my external hard drive but for some reason my computer recognizes it for about a minute and then stops. this is the dmesg i get when i plug it in :
[69898.760000] scsi16 : SCSI emulation for USB Mass Storage devices

[69898.760000] usb-storage: device found at 11

[69898.760000] usb-storage: waiting for device to settle before scanning

[69903.760000] usb-storage: device scan complete

[69903.988000] scsi 16:0:0:0: Direct-Access     HITACHI_ DK23FA-80        00M3 PQ: 0 ANSI: 0

[69903.996000] SCSI device sdb: 156301489 512-byte hdwr sectors (80026 MB)

[69904.000000] sdb: Write Protect is off

[69904.000000] sdb: Mode Sense: 00 08 00 00

[69904.000000] sdb: assuming drive cache: write through

[69904.004000] SCSI device sdb: 156301489 512-byte hdwr sectors (80026 MB)

[69904.008000] sdb: Write Protect is off

[69904.008000] sdb: Mode Sense: 00 08 00 00

[69904.008000] sdb: assuming drive cache: write through

[69904.008000]  sdb: sdb1

[69904.424000] sd 16:0:0:0: Attached scsi disk sdb

[69904.424000] sd 16:0:0:0: Attached scsi generic sg2 type 0

[69934.640000] usb 4-2: reset full speed USB device using uhci_hcd and address 11
[70093.604000] sd 16:0:0:0: SCSI error: return code = 0x00050000

[70093.604000] end_request: I/O error, dev sdb, sector 156301488

[70093.604000] printk: 363 messages suppressed.

[70093.604000] Buffer I/O error on device sdb, logical block 156301488

[70118.572000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

i have no idea whats going on because im new to ubuntu so if someone could help me out i would greatly appreciate it.

---

### Post by taurus on 2007-05-05
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by tgalati4 on 2007-05-05
If this is a new disk, especially a Hitachi DeathStar, then they need to be broken in before they work properly.  Try a disk utility to erase the free space to get the disk exercised enough for reliable operation.  It looks like the disk is having problems reading a few sectors.  Sometimes the disk just needs to warm up.  Once it is up to operating temperature it will work fine.  Maybe.

Try a different USB cable.  They are not all the same.  Take out any kinks and route it away from interference sources.

---

### Post by tuki on 2007-05-05
when i put sudo fdisk -l i get 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

---

### Post by tuki on 2007-05-05
i've had this hard drive for a while now, i have info there from before when i use to have windows and i never had any problems with it

---

### Post by tgalati4 on 2007-05-05
Time to get into some details of the drive:

sudo apt-get install smartmontools
sudo smartctl -s on /dev/sdb
sudo smartctl -t short /dev/sdb
sudo smartctl -l selftest /dev/sdb
sudo smartctl -a /dev/sdb

Post the results from the above.  As an external drive, it has probably been seen some bumps in its time.

To perform a long test on the drive:  (takes about an hour!)
sudo -t long /dev/sdb
sudo -l selftest /dev/sdb

Good luck.

---

### Post by tuki on 2007-05-05
tuki@tuki-laptop:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smartmontools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tuki@tuki-laptop:~$ sudo smartctl -s on /dev/sdb
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory
tuki@tuki-laptop:~$ sudo smartctl -t short /dev/sdb
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory
tuki@tuki-laptop:~$ sudo smartctl -l selftest /dev/sdb
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory
tuki@tuki-laptop:~$ sudo smartctl -a /dev/sdb
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory

that's what i get when i type that.

---

### Post by tgalati4 on 2007-05-05
Brainfart!  

I forgot, smarttools does not work through USB!

You can only get smartctl to communicate through the IDE or SATA data bus.  USB is a simpler protocol and does not pass the necessary data.

If I had a drive like this, I would remove it from it's USB case, and plug it directly to an IDE ribbon cable of a desktop PC and run smartctl to see what is going on.

I'm sorry to waste your time.

You need to find a Windows machine and load the Hitachi DeathStar utilities and run the diagnostic tests. 

If the drive is past warranty then pull it out of its case and treat it as an internal drive and run the smartctl tests.

If you have a mac, then plug in the USB and run the Disk Utilities and run the verify routine on each partition and "erase free space".  Any errors will show up quickly.

Good luck.

---

