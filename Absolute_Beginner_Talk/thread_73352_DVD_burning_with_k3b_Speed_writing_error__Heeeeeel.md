---
title: "DVD burning with k3b: Speed writing error ??? Heeeeeelp"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-08
Devices
-----------------------
TOSHIBA DVD-ROM SD-R6112 1332 (/dev/hdc, ) at /mnt/hdc [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
/dev/hdc: engaging DVD-R DAO upon user request...
:-( Failed to change write speed: 2117->2700

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/hdc -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=dao -dvd-compat -speed=1 -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3b38ocma.tmp -rational-rock -hide-list /tmp/kde-root/k3bHgScEb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-root/k3bEI1uFb.tmp

---

