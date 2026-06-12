---
title: "Which apt-get are recommanded to install k3b?"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-10
I did only :
  
apt-get install k3b 
  
  
(also cddao
dvd-tools)
 
Is it enough ? Do I need additional 'apt-get' or 'dpkg -i' ??

Thank you

---

### Post by Leif on 2005-10-10
have you enabled universe and multiverse as detailed in ubuntuguide.org ? and it should be "sudo apt-get install k3b"

---

### Post by Perfect Storm on 2005-10-10
Nope, that looks fine.
When installing apt-get install k3b all its dependency will be install as well
the same goes for cdrdao.

---

### Post by poofyhairguy on 2005-10-10
[https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29](https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29)

---

### Post by patrick295767 on 2005-10-10
[QUOTE=Leif]have you enabled universe and multiverse as detailed in ubuntuguide.org ? and it should be "sudo apt-get install k3b"[/QUOTE]

I'll look for "universe and multiverse " in the ubuntuguide.org and let you know ... 
thank you very much !!

Patrick

---

### Post by patrick295767 on 2005-10-10
[QUOTE=patrick295767]I did only :
  
apt-get install k3b 
  
  
(also cddao
dvd-tools)
 
Is it enough ? Do I need additional 'apt-get' or 'dpkg -i' ??

Thank you[/QUOTE]


that's the error message : " change speed ":
(growiso and cddao are installed)

Devices
-----------------------
TOSHIBA DVD-ROM SD-R6112 1332 (/dev/hdc, ) at /mnt/hdc [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version: 3.3.3
Kernel: 2.6.10-5-386

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
/dev/hdc: engaging DVD-R DAO upon user request...
 Failed to change write speed: 2117->2700

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/hdc -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=dao -dvd-compat -speed=1 -gui -graft-points -volid K3b data project -volset -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3b38ocma.tmp -rational-rock -hide-list /tmp/kde-root/k3bHgScEb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-root/k3bEI1uFb.tmp

thank you

---

