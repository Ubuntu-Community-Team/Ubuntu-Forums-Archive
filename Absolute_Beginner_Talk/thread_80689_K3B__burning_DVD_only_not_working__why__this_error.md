---
title: "K3B : burning DVD only not working ?? why ? this errormsg"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-22
Devices
-----------------------
LITE-ON LTR-48125W VS06 (/dev/scd0, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
TOSHIBA DVD-ROM SD-R6112 1332 (/dev/hdc, ) at /mnt/hdc [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; RAW/R96R]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
:[COLOR="Black"]**-( Failed to change write speed: 2117->2700**[/COLOR]

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=1 

mkisofs
-----------------------
/usr/bin/mkisofs: Warning: -follow-links does not always work correctly; be careful.
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
/usr/bin/mkisofs: Connection reset by peer. cannot fwrite 2048*1

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.23 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.23 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3b0Ag3Zb.tmp -rational-rock -hide-list /tmp/kde-root/k3bp9wi4b.tmp -full-iso9660-filenames -follow-links -iso-level 2 -path-list /tmp/kde-root/k3bWi90pb.tmp -dvd-video /tmp/kde-root/k3bVideoDvd0 /root/.kde/share/apps/k3b/temp/dummydir0/ 
 
  
 
 
my fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hda3	/mnt/hda3	ntfs	defaults,rw,user,umask=000	0	2
/dev/hda1	/mnt/hda1	vfat	defaults,rw,user,umask=000	0	0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5	/mnt/hda5	ntfs	defaults,rw,user,umask=000	0	2
/dev/hdc	/mnt/hdc	auto	user,noauto,ro,unhide	0	1
/dev/sda1	/mnt/sda1	auto	user,noauto,rw,unhide	0	1

---

### Post by patrick295767 on 2005-10-25
I tried "Ignore"  speed 
instead of AUTO
  
and it worked !!
  
The reason comes from the hardware... some people should have same experience with laptop toshiba...

---

