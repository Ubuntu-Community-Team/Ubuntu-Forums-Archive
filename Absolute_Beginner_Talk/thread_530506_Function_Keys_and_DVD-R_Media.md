---
title: "Function Keys and DVD-R Media"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Subcontinental on 2007-08-20
Right now the only things that are preventing me from completely getting rid of Windows in favor of Ubuntu are that I cannot get my function keys to work, and blank DVD-R media cannot be recognized.  I have a Toshiba Satellite M45-S331.

Function Keys:

I have fnfxd, toshset, and toshutils installed but only a few function keys work correctly (FN + F5/F10/F11).  However, the most important ones to me are FN + F6/F7 (they control my LCD brightness).  How can I get these keys to work correctly?

DVD-R Media:

When I insert a blank DVD-R into my drive, neither Ubuntu or Windows will recognize it.  Thus, I cannot burn anything on these DVDs.  The same set of DVD-R media used to work fine before I installed Ubuntu, but now they won't work. They also work just fine in my father's laptop, but he does not have Ubuntu.  DVD+R works just fine, but I ran out of those and I have a 100 pack of DVD-Rs that I bought for a few bucks on Black Friday that I'd like to use.  I uninstalled and reinstalled the DVD±RW tools through the synaptic package manager, but that still didn't work.  How can I get this fixed?

Thanks for any feedback.

---

### Post by Subcontinental on 2007-08-21
Ok now my CD/DVD writer burns absolutely nothing, but I have been able to burn files before in Ubuntu.  Here is my debug output:

> System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-830S 1.00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-830S '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 4234 KB/s
Track 01: data   692 MB        
Total size:      795 MB (78:48.30) = 354623 sectors
Lout start:      795 MB (78:50/23) = 354623 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 5226
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 15 12 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 9.477s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:   13.106s
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -dao driveropts=burnfree -eject -data -tsize=354623s - 



---

### Post by Subcontinental on 2007-08-21
Ok, forget about the DVD-R problem.  It seems as if my DVD burner will only do DVD+R and RWs...](*,)
Now I want to get a cheap external DVD burner because I don't want this 100 pack going to waste.  Which one would you recommend?  Also I still have the problem with my function keys not working correctly.  If there is a way to manually turn down/up the brightness then I would be happy with that way too.  Thanks for putting up with me.  =P

---

