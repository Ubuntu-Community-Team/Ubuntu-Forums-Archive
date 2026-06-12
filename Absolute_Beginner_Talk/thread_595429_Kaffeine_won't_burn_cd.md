---
title: "Kaffeine won't burn cd"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mcmakin50 on 2007-10-28
I have Kubuntu 7.10 and I can't burn any data to CD.  
Here is the error log:
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
CyberDrv CW088D CD-R/RW 15HF (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

JLMS XJ-HD166S DPS6 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 341.774s timeout 200s
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'CyberDrv'
Identification : 'CW088D CD-R/RW  '
Revision       : '15HF'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
FIFO size      : 12582912 = 12288 KB
/usr/bin/wodim: Cannot load media.
Track 01: data   695 MB        
Total size:      798 MB (79:05.48) = 355911 sectors
Lout start:      798 MB (79:07/36) = 355911 sectors

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd1 speed=36 -dao driveropts=burnfree -overburn -data -tsize=355911s - 

I was trying to burn the iso image of Edubuntu.

any assistance would be appreciated.

John

---

