---
title: "Firmware of my dvd-ram"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-09-22
How do I figure it out which firmware is in my dvd-ram???

I have a Satellite a135-s4656 laptop, and it comes with Matshita UJ-850s dvd ram...

And I am wondering which firmware is installed, if it is a RPC1 or RPC2...

And if it is RPC2 how do I change it to RPC1?

Thank you...

---

### Post by southernman on 2007-09-22
In a terminal type this command:

```
sudo hdparm -I /dev/?d?
```

Replace the "?" above with the proper letters of your dvd drive... Could be hda,b,c, or d or else sda,b,c or d

---

### Post by brunoskrebs on 2007-09-22
hmmmm I couldnt find it...
I tried with all the sda ( sda, sda1, sda2, sda 3, sda 4 and sda 5) but they all talk about my HD. So I tried with scd0 as well and it sais:
 > root@bruno:/dev# hdparm -I scd0

scd0:
 HDIO_DRIVE_CMD(identify) failed: Input/output error
root@bruno:/dev# 


---

### Post by likemindead on 2007-10-10
I have a MATSHITA UJ-811 DVD-RW drive and I cannot burn anything!!! Please help. I'm trying to burn an Ubuntu disc for a friend. Here's what I get from GnomeBaker:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-811  '
Revision       : 'H102'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
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
Drive buf size : 1343488 = 1312 KB
FIFO size      : 12582912 = 12288 KB
locks total: 359846 Blocks current: 359846 Blocks remaining: 175217
Starting to write CD/DVD at speed   8.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.Speed set to 1411 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 32 00 10 03 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x03 Qual 0x00 (peripheral device write fault) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 11.302s timeout 60s
wodim: OPC failed.
Writing  time:   15.028s
BURN-Free was never needed.

```

:confused:

---

