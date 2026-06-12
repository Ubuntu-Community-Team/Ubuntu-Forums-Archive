---
title: "K3B problem.. again.."
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by topic58 on 2006-04-08
Hi all, I posted a thread a week ago about K3b. The problem is that K3b thinks my CD/DVD-burner wants double-layer DVD:s. I tried to play a double-layer DVD a week ago. And after that K3b went crazy. No way I can burn or erase RW or R. Can someone please help me out with this problem?? There must be a way to change some settings in a file back to single-layer... Tried to uninstall and then re-install K3b, with no success. Maybe a .conf-file somewhere?? Before trying a double-layer DVD everything was smooth with K3b. Getting desperate here - so please help me out someone! I have used Nautilus for DVD-burning the last couple of days, but I can't erase RW in Nautilus. And Gnomebaker doesn't work for me. Using Ubuntu Breezy and Gnome. My burner is a TSSCorpCD/DVDW-TS-H552U.
When trying to erase a DVD-RW I got this message in K3b:
System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
TSSTcorp CD/DVDW TS-H552U US02 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=15 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-10-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
/usr/bin/X11/cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
/usr/bin/X11/cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identifikation : 'CD/DVDW TS-H552U'
Revision       : 'US02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0014
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 (current)
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD/DVD driver (checks media) (mmc_cd_dvd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1376256 = 1344 KB
Current Secsize: 2048
Waiting for drive to calm down.
Starting to write CD/DVD at speed 15 in real force BLANK mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 51 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x51 Qual 0x00 (erase failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 13.993s timeout 9600s
Starting to write CD/DVD at speed 15 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.
/usr/bin/X11/cdrecord: Some drives do not support all blank types.
/usr/bin/X11/cdrecord: Try again with cdrecord blank=all.
This drive or media does not support the 'BLANK media' command

---

### Post by patrick295767 on 2006-04-08
My k3b error msg : [http://www.ubuntuforums.org/showthread.php?t=151509&highlight=k3b](http://www.ubuntuforums.org/showthread.php?t=151509&highlight=k3b)
>  System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version: 3.3.4
Kernel: 2.6.12-9-386
Devices
-----------------------
LITE-ON DVDRW SHW-1635S YS0F (/dev/hdd, ) at /mnt/hdd [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

Used versions
-----------------------
growisofs: 5.21
mkisofs: 2.1-unofficial-iconv

growisofs
-----------------------
unable to pread64(2) primary volume descriptor: Input/output error
you most likely want to use -Z option.

growisofs command:
-----------------------
/usr/bin/X11/growisofs -M /dev/hdd -use-the-force-luke=notray -use-the-force-luke=tty -gui -graft-points -volid K3b data project -volset -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-celina/k3bDzmhwb.tmp -rational-rock -hide-list /tmp/kde-celina/k3bOODBKb.tmp -joliet -hide-joliet-list /tmp/kde-celina/k3b0DaQoa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-celina/k3b0oJgDa.tmp

---

### Post by patrick295767 on 2006-04-08
Did you try to burn with IGNORE ???
  
That's working on one of my configs ... and only way to burn dvd .. 

Greetz

---

### Post by topic58 on 2006-04-08
Tried ignore. After that I got this long System message. (after trying to erase a DVD-RW that is) When trying to write a DVD-R it seem to work, no errors. But when trying to read the DVD-R after burning it's empty.
I got this message in KDE-forum: Open your home folder, and select "View -> Show hidden files". Then look for either '.k3b', or '.kde/share/apps/k3b'. Just rename that folder, to reset k3b back to its defaults.
[http://www.ubuntuforums.org/showthread.php?t=157025](http://www.ubuntuforums.org/showthread.php?t=157025)

---

