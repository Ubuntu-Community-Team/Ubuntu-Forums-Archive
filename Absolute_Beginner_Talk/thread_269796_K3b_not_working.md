---
title: "K3b not working"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-10-02
The first time I tried to use K3b it didn't work. Recently though (this morning) I used it to burn a data folder onto a CD. It worked fine without any problems. I am now trying to do exactly the same task (same folder!) and it is not working!
The "debugging output" says this, and I have no idea what it might mean:

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
MATSHITA UJDA340 1.00 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; SAO/R96P; SAO/R96R]

K3b
-----------------------
Size of filesystem calculated: 342058

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'MATSHITA'
Identifikation : 'UJDA340         '
Revision       : '1.00'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
Drive buf size : 1359872 = 1328 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   668 MB        
Total size:      767 MB (76:00.77) = 342058 sectors
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Lout start:      767 MB (76:02/58) = 342058 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11849 (97:24/01)
  ATIP start of lead out: 359847 (79:59/72)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 25
Manufacturer: Taiyo Yuden Company Limited
Blocks total: 359847 Blocks current: 359847 Blocks remaining: 17789
Starting to write CD/DVD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: WARNING: Drive returns wrong startsec (0) using -150
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0C 00 00 00 00 64 C0 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x64 Qual 0xC0 (illegal mode for this track) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 3.131s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 0 K BSize: 1525 K
Starting new track at sector: 0
Track 01:    0 of  668 MB written.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0C 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.001s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   16.077s
Average write speed 560.1x.
Fixating...
Fixating time:    0.006s
/usr/bin/X11/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=8 -dao driveropts=burnfree -eject -data -tsize=342058s - 

mkisofs
-----------------------
342058
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.15% done, estimate finish Mon Oct  2 23:06:12 2006
  0.30% done, estimate finish Mon Oct  2 23:06:12 2006
  0.44% done, estimate finish Mon Oct  2 23:06:12 2006
  0.59% done, estimate finish Mon Oct  2 23:06:12 2006
/usr/bin/X11/mkisofs: Connection reset by peer. cannot fwrite 32768*1

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-justin/k3bE1gUOb.tmp -rational-rock -hide-list /tmp/kde-justin/k3bVePEda.tmp -joliet -hide-joliet-list /tmp/kde-justin/k3br482Zb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-justin/k3b2f7hzb.tmp 




Any help would be great in getting this thing to work!
Thanks
Justin

---

### Post by bluefrog on 2006-10-02
I had the same problem.

Have installed brasero (don't remember if I did it from universe or directly from the site).

Not sure if brasero is not using cdrecord (in which case I do not know what is using....) but now my cd can be erased and burnt again)

James

---

### Post by Marsolin on 2006-10-02
Try reinstalling [cdrecord]("http://linuxappfinder.com/package/cdrecord"). I had a similar unable to set UID error and the reinstall fixed it.

---

### Post by woodlandjustin on 2006-10-02
> **Marsolin said:**
> Try reinstalling [cdrecord]("http://linuxappfinder.com/package/cdrecord"). I had a similar unable to set UID error and the reinstall fixed it.

Thanks. How do I do that?
Justin

---

### Post by Marsolin on 2006-10-03
To reinstall you can open Synaptic and search for [cdrecord]("http://linuxappfinder.com/package/cdrecord"). There will be green box to the left of the name once it has been found. Left click that box and select Mark for Reinstallation. Click Apply and that should do it.

---

