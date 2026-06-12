---
title: "OPC error in k3b ??"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by xnszxdotnet on 2005-09-13
can and i tell me what is error is about? how to fix it.

I install k3b and had it working just fine now it's doing this. here is the saved debugging ouput.



Devices
-----------------------
PIONEER DVD-RW  DVR-107D 1.10 (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]

System
-----------------------
K3b Version: 0.11.24
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hda obs=32k seek=0'
:-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error

growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/hda=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=4 

mkisofs
-----------------------
/usr/bin/mkisofs: Warning: -follow-links does not always work correctly; be careful.
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
/usr/bin/mkisofs: Connection reset by peer. cannot fwrite 2048*1



mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid MONSTER -volset  -appid K3B THE CD KREATOR VERSION 0.11.24 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.24 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-booger/k3bVpLeTb.tmp -rational-rock -hide-list /tmp/kde-booger/k3b4hMPoc.tmp -full-iso9660-filenames -follow-links -iso-level 2 -path-list /tmp/kde-booger/k3bHYE6kb.tmp -dvd-video /tmp/kde-booger/k3bVideoDvd0 /home/booger/.kde/share/apps/k3b/temp/dummydir0/

---

### Post by lakcaj on 2005-10-15
Just want to post in here because I'm having the exact same issue.  This is on a debian sarge machine, but debian and ubuntu are very similar, so I'm hoping the solution to the problem is the same.  If I find out anything, I'll post the answer here.  Also, if you fix the problem, please post the solution here as well.

---

### Post by Klefgodofbalance on 2006-03-19
I am having the same problem.  I am running kubuntu and found posts saying that the media is the cause of this problem, but i have tried three differnt DVD-R's with out any luck. I am really hoping someone knows what is going on.

---

### Post by darknightuk on 2006-05-05
same prob here what  kernel version's are the other posters using using also what drive and media brand and type?
am using kernel 2.6.15-21-k7 and a pioneer 108 drive

EDIT:-didn't notice the age of the orginal post!

---

### Post by -DarkMind- on 2006-08-12
same problem here :(  with SONY DVD-RW DRU-820A

---

