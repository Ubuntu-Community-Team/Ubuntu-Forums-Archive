---
title: "I don't know how to use GnomeBaker????"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-07-25
So there I am.. installing GnomeBaker to burn an Ubuntu CD...

I use the "Burn CD Image" tool... with all default settings and CDs I've never had a problem with... I tried burning 3 times.. turned all of the CDs into coasters.. can someone tell me what I'm doing wrong? Here's a transcript of what happened on the 3rd time (which I suspect happened 2 other times).

> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '3,0,0'
scsibus: 3 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H62N '
Revision       : 'CL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 16932 kB/s 96x CD 12x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 9B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.002s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 317440 bytes
Writing  time:   15.026s
Average write speed 317.3x.
Fixating...
Fixating time:   18.616s

---

### Post by shoaibi on 2007-07-25
Well if you are Windows user and shifting to Ubuntu for the first time, i recommend you to use NeroLinux whose interafce is quite familiar to Ner for windows, but Nero linux is licensed, 
i personally use K3b on Ubuntu and it rocks....

---

### Post by someguy91 on 2007-07-25
heh fair enough I'll give it a look. I would still like to know whats wrong with GnomeBaker though... the process seemed fairly.. straightforward.. I don't know what's causing the errors.

---

### Post by shoaibi on 2007-07-25
i am off the box right now, moving between places, so connecting remotely and reply you, will have a detailed look at you post in some time. Sorry...


Anybody else got some time?

---

