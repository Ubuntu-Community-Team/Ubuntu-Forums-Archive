---
title: "Already burning a CD with 1x speed but it still says try a lower speed"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by doowgof on 2007-11-26
I was trying to write an iso file to a CD-R with the CD/DVD Creator. I chose 1x for the speed but after I clicked on write my cd just turns awhile and then an error message said Error while writing to disk. Try a lower speed.
What shall I do?

---

### Post by jken146 on 2007-11-26
Weird.  Maybe try a different burning program, like k3b.

---

### Post by anaconda on 2007-11-26
Sounds like a harware error.. Maybe your CD/DVD writer is going bad? Does it work in other os:s?

---

### Post by doowgof on 2007-11-26
> **anaconda said:**
> Sounds like a harware error.. Maybe your CD/DVD writer is going bad? Does it work in other os:s?

It does work in XP before I wipe it off..
I'm trying with GnomeBaker now, hopefully it works.

---

### Post by doowgof on 2007-11-26
What does Dummy write and burnfree mean in Gnomebaker?

---

### Post by doowgof on 2007-11-26
I used Gnomebaker and this is the error message:
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'UJDA750 DVD/CDRW'
Revision       : '1.51'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1433600 = 1400 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 14.739s timeout 60s
wodim: OPC failed.
Writing  time:   16.996s
BURN-Free was never needed.
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.


....What's now?

---

### Post by doowgof on 2007-11-26
I used k3b and chose the min speed 2x, the following error message appeared:
[IMG]http://img405.imageshack.us/img405/1758/screenshotburningiso966vu5.png[/IMG]

---

### Post by doowgof on 2007-11-26
K  finally it worked.
I used k3b and chose auto for speed, therefore it chose 24x to write the disk.... The estimate speed it said was around 12x and then increased to 16x................ The average speed was 14.05x.
This is not what I want.. Cos I want to burn an Debian installing disk with a low burning speed....
Will it really affect my installation? Cos I had that experience before.. The DVD-R (I'm using CDR this time) was burnt using high speed therefore the system couldn't mount it in installation.

---

### Post by Jerry N on 2007-11-26
I created a couple dozen bootable disks from ISOs and have never used a speed lower than 40x.  If it is necessary to lower the speed, I think there is a problem with the software, the media, or with the drive.  (most of these were burned with Nero, using a Samsung or LG CD/DVD writer).  

Jerry

---

