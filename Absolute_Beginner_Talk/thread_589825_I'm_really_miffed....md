---
title: "I'm really miffed..."
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Hraefn on 2007-10-24
I'm trying to burn a fresh .iso disk on my laptop, and it's not working.  I've tried K3B and Gnomebaker, and nothing.

This is what I got from k3b:

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4240N 0H22 (/dev/scd0, /dev/sg1) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4240N'
Revision       : '0H22'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1705200 = 1665 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1764 KB/s
Track 01: data   678 MB        
Total size:      778 MB (77:09.76) = 347232 sectors
Lout start:      779 MB (77:11/57) = 347232 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 12617
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 1665 K BSize: 1665 K
Starting new track at sector: 0
Track 01:    0 of  678 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.007s timeout 200s
/usr/bin/wodim: The current problem looks like a buffer underrun.
/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/wodim: Please report.
/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 0 bytes
Writing  time:   14.033s
Average write speed 444.9x.
Fixating...
Fixating time:    0.011s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -eject -data -tsize=347232s - 

I thought it was the CD-RWs I had bought, so I decided to get a stack of CD-Rs instead.  No such luck.  I've got a sneaking suspicion it has to do with settings and my laptop's burner, which is a cross between LG and Hitachi (I think) made for many many laptops during the early 2000s.

Vendor_info    : 'HL-DT-ST'
Identification : 'RW/DVD GCC-4240N'
Revision       : '0H22'

I know there was a firmware update for this burner, but I have no idea how to install such beasts in linux, and I'm not sure if there's a work-around out there in the community.  I know I'm not the only one with this burner, and I know I'm not the only one with this issue.  Any help???  Pls/Thx :)

-Hraefn

---

### Post by Maestro23 on 2007-10-24
Got a link to the firmware?

---

### Post by blackaardvark on 2007-10-24
have you tried just right clicking on the iso and choosing write to disk? i know had all manner of problem with other programs but that works just fine for me..

---

### Post by Hraefn on 2007-10-24
Look [Here]("http://tdb.rpc1.org/#GCC4240N") for the 4240 that I've got.

This is the closest I could find for the firmware (and I see an update there, too, but haven't the foggiest as to how to use it.

I've tried burning the ISO file from Thunar...uses Brasero, which doesn't work well for me.

Thanks for the help, though

Also, how does one fix a buffer under-run and enable DMA? That also shows up often (as also seen above in the original post)

---

