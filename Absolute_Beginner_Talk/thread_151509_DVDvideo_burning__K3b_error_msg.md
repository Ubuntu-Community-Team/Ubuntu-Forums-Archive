---
title: "DVDvideo burning : K3b error msg"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-28
The K3B gives such error while trying dvd burning 
(ignore and auto speed gave same results)

Would have someone any idea ?

Thank; you very much !

Patrick

> System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
LITE-ON DVDRW SHW-1635S YS0F (/dev/hdd, ) at /mnt/hdd [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

Used versions
-----------------------
growisofs: 5.21
mkisofs: 2.1-unofficial-iconv

growisofs
-----------------------
:-( unable to pread64(2) primary volume descriptor: Input/output error
    you most likely want to use -Z option.

growisofs command:
-----------------------
/usr/bin/X11/growisofs -M /dev/hdd -use-the-force-luke=notray -use-the-force-luke=tty -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-celina/k3bDzmhwb.tmp -rational-rock -hide-list /tmp/kde-celina/k3bOODBKb.tmp -joliet -hide-joliet-list /tmp/kde-celina/k3b0DaQoa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-celina/k3b0oJgDa.tmp 

---

