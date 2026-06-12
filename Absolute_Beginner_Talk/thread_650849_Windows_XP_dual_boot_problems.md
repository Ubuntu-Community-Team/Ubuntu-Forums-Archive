---
title: "Windows XP dual boot problems"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by hazelmae on 2007-12-26
Hi, I'm new to Linux, and cannot seem to get grub to boot my windows XP.

I have two SATA drives, the first of which has the windows installation.  The second is for data storage.  I have added an IDE drive onto which I have installed Ubuntu.  Grub boots Ubuntu without problem, and I have sucessfully mounted the windows partitions using the diskmounter script.

The SATA drives were disconnected during the installation to protect my data and windows.  Grub has been installed to the IDE drive, and the bios changed to boot from HDD0 (IDE)  instead of the SATA.  When I change this setting back, windows boots normally.

results of fdisk -l :

```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba6331d5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+  83  Linux
/dev/hda2            2433        2681     2000092+  82  Linux swap / Solaris
/dev/hda3            2682        9964    58500697+   b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf507f507

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       30400   162264532+   f  W95 Ext'd (LBA)
/dev/sda5           10200       30400   162264501    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01ba01ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       14592    76252522+   f  W95 Ext'd (LBA)
/dev/sdb5            5100       14592    76252491    7  HPFS/NTFS

```

contents of /boot/grub/menu.lst:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2982a5ee-9bb4-4cae-be48-e6371f51f766 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2982a5ee-9bb4-4cae-be48-e6371f51f766 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

contents of /boot/grub/device.map:

```


(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb


```




Can anyone please help me figure out what's wrong?

---

### Post by Jack78 on 2007-12-26
It looks like grub is trying to boot windows from hd1,0, although your windows installation is on /dev/sda1.  If you change all the HDs to SDs will it work?

---

### Post by jas0 on 2007-12-26
Try replacing the Windows section in your boot.lst file with the bare essentials (back up the file first of course):

```
title Windows XP
root (hd1,0)
makeactive
chainloader +1

```

---

### Post by meierfra on 2007-12-26
try

title		Windows XP
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


and if that did not work

title		Windows XP
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Alternatively you can change the  boot order in the bios, but leave the IDE drive in the first position

---

### Post by kenboyles72 on 2007-12-26
I have the exact same setup, two sata drives (1 xp, 1 storage) and an ide with ubuntu. this is what is in my grub list:

title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by hazelmae on 2007-12-27
Thanks for the help everyone.  Unfortunately none of the above suggestions worked.

All of the proposed changes to menu.lst resulted in no change.  The system shows "system loading" in white letters on a black screen, then hangs.  The only exceptin was Jack78's suggestion to replace all hd entries with sd.  This resulted in an "error while parsing number".

meierfra, could you explain what you mean about changing the boot order in the bios?  I don't think I understand what you mean.  Currently, my boot sequence is Floppy, CDrom, HDD0.  It used to be Floppy, CDrom, SCSI (sata), and if I return to this boot sequence, the windows bootloader comes up and loads windows, bypassing grub completely.

I tried changing the boot order to CDrom, HDD0, SCSI, but it had no effect.  changing it to CDrom, SCSI, HDD0 causes windows to boot directly, bypassing grub.

Kenboyles72, could you post the contents of your /boot/grub/devices.map?

---

### Post by meierfra on 2007-12-27
I wanted you to switch the order between the two SATA   drives. But it  seems your  BIO's don't let you do that.   I'm I little puzzled that none of my suggestions worked. Try

title Microsoft Windows XP Home Edition
root (hd0,2)
savedefault
makeactive
chainloader +1

---

### Post by kenboyles72 on 2008-01-01
Sorry I didn't get back sooner. Here is what's in devices.map:

```
(hd0)	/dev/hdc
(hd1)	/dev/sda
(hd2)	/dev/sdb
```

I don't know if you got the problem fixed, but you could take a look [[COLOR="Red"]HERE[/COLOR]]("http://sidvind.com/wiki/HOWTO_Restore_GRUB_after_Windows_XP_installation-cd"). It tells how to reinstall grub. Though it's for gentoo, it should be the same for ubuntu. I also found this for restoring grub for ubuntu:

> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

