---
title: "Unable to mount USB 2.0 external hard drive"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by jacaronda on 2008-01-06
I just plugged a new Toshiba USB 2.0 external into my desktop system running Ubuntu 6.06 and nothing appears on the desktop.  Under Places ... Computer, it shows up as "Toshiba USB 2.0 Drive R00", but trying to open or mount it results in "Unable to mount the selected volume".  Details:

mount: no medium found
mount: no medium found
error: could not execute pmount

 I tried "sudo fdisk -l" in a terminal but the 160GB Toshiba external drive does not appear at all.  

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        4762    18715725   83  Linux
/dev/hda3            4763        4865      827347+   5  Extended
/dev/hda5            4763        4865      827316   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    7  HPFS/NTFS

The drive works fine plugged into a laptop running Windows Vista.  I don't know if it's NTFS or FAT32.

I tried following the instructions at [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009), but after updating and upgrading my system, got stuck at 

sudo apt-get install ntfs-config

 "Couldn't find package ntfs-config".   Seems like I'm off track here since fdisk doesn't even see the drive.

Please, any help would be most appreciated.

Thanks

---

### Post by metalpancake on 2008-01-06
I think gparted may help, but i don't know because I';ve never used it before!

---

### Post by jacaronda on 2008-01-06
Can anybody help please? This drive  mounts on both Windows and Mac  laptops, so I guess it's FAT32.  The drive doesn't show up on the desktop or with 'fdisk -l'.  Below is some more info that might help diagnose the problem.  I've searched the forums for info about driver 'sd' needing updating and no clues there either.  I'm assuming my USB port is 2.0  since USB 2.0 shows up in the Device Manager and the blue light on the drive lights up when it's plugged in

jack@ubuntu:~$ lsusb
Bus 004 Device 025: ID 0930:a000 Toshiba Corp.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

jack@ubuntu:~$ dmesg | tail
[17183717.592000] usb-storage: waiting for device to settle before scanning
[17183722.592000]   Vendor: Toshiba   Model: USB2.0 Drive R00  Rev: 1.43
[17183722.592000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183722.600000] usb-storage: device scan complete
[17183722.680000] Driver 'sd' needs updating - please use bus_type methods
[17183722.704000] sd 2:0:0:0: Attached scsi removable disk sda
[17183722.728000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17183783.188000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17183783.188000] SGI XFS Quota Management subsystem
[17183783.240000] JFS: nTxBlock = 3779, nTxLock = 30238

jack@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by kdoyle on 2008-03-01
I am having this exact same problem.  My dmesg | tail output is differet but neither fdisk or gparted detect the hard drive or device at all and no sda entry is even created in the /dev/ folder.  Does anyone have any ideas or did you figure it out jacaronda?

---

