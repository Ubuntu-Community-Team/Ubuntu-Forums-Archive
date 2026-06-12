---
title: "Ubuntu ATI Radeon Live CD. 600x400"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by squiggs on 2007-11-28
Should I use the Alternate CD to get this to work? I've booted the live cd and it runs at 640x480 preventing hard disk install. Also running a command at the terminal tells me that SDB has no valid partition table. Will my hard disk install work - I tried an alternative flavour of Linux (MINT) and it died when trying to load GRUB. This was to do with the hard disks I think..but to be sure I'm posting the fdisk here...as Im hesitating as to whether to bother installing to my hard disk. Any advice on potential implications welcome. I'm trying to catch any potential problems early rather than firefighting..

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd5ecd5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8624    69272248+   7  HPFS/NTFS
/dev/sda2            8625        8996     2988090    5  Extended
/dev/sda3            8997       17749    70308472+   7  HPFS/NTFS
/dev/sda5            8625        8996     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05000000

Disk /dev/sdb doesn't contain a valid partition table
ubuntu@ubuntu:~$

---

### Post by luisfcup on 2007-11-29
I don't know about the disk, but to fix the resolution you can try altering the xorg.conf file in /etc/X11
I had a similar problem with a Targa laptop with an ATI card.
Edit the xorg.xonf file and in: Section "Screen" put the modes you what for resolution.
```
Section "Screen"
 Identifier "Default Screen"
 Device "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
 Monitor "Monitor Generico"
 DefaultDepth 24
 SubSection "Display"
  Depth 16
  Modes **"1680x1050"**
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes **"1680x1050"**
 EndSubSection
EndSection

```

You also may need to put in the Section "Device" the following:
```
Option "MonitorLayout" "LVDS,Auto"
```
See [Bug report #22985]("https://launchpad.net/xserver-xorg-driver-ati/+bug/22985")

After altering the file reload the x-server with <Ctrl>+<Alt>+Backspace, don't restart with the live cd or the changes you made will be lost :p

---

