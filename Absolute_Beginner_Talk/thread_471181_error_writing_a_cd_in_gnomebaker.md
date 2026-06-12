---
title: "error writing a cd in gnomebaker"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-06-11
This is the error message 

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
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H10N '
Revision       : 'JL10'
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
Drive DMA Speed: 12774 kB/s 72x CD 9x DVD
FIFO size      : 12582912 = 12288 KB
 Speed set to 8467 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 01 B0 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.002s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 1016064 bytes
Writing  time:   14.112s
Average write speed 335.6x.
Fixating...
Fixating time:   18.162s

Thanks 

Stephen

---

### Post by prof.morbius on 2007-06-15
I can't help, but I have the exact same problem with the same drive.  Further, when I run ```
sudo hdparm /dev/scd0
``` I get the following:
> /dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


I'd love to get this fixed, if anyone has any ideas.  I've already read through the [Burner not working in 7.04]("http://ubuntuforums.org/showthread.php?t=434443") thread, but the nautilus-cd issue mentioned on page 2 doesn't affect me, and the 2.6.20-16 move didn't do the trick either.

---

### Post by crimesaucer on 2007-07-17
I have the same problem with GnomeBaker running on my xubuntu:

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
Identification : 'DVD-RW GWA-4082N'
Revision       : 'CC15'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 9216 kB/s 52x CD 6x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 5D 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 06 90 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.002s timeout 40s
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 190464 bytes
Writing  time:   15.811s
Average write speed 282.3x.
Fixating...
Fixating time:   79.709s




###############################################33

Any way to fix this or should I use a different burner.

---

### Post by moron on 2007-07-21
I'm using K3B but am getting the exact same symptoms.  In my case K3b fails after an arbitrary amount of time burnind a CD.  Looking at the error log I eventually see this error:

Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error

It seems unlikely that my drive has died since it is only a couple of months old and has not seen heavy use. There was a K3B related system update recently if memory serves (security related) so possibly that fubar'd something?

I show the following if I run "hdparm -i":

/dev/scd0:

 Model=TSSTcorpCD/DVDW SH-S183L                , FwRev=SB01    , SerialNo=      
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode

Cheers

---

### Post by Ynem on 2007-07-23
got this cryptic message when trying to burn a .cue image file.
can someone tell me what it's all about?

1,0,0: SONY DVD RW DRU-700A	Rev: VY03
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Starting write at speed 24...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
Turning BURN-Proof on
Enabling JustSpeed.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot setup write parameters for session-at-once mode.
ERROR: Please try to use the 'generic-mmc-raw' driver.
ERROR: Writing failed.

---

### Post by daradib on 2007-08-22
I get the same problems as halesquad and prof.morbius when using K3B, GnomeBaker, or Serpentine (I can't get anything to burn).

I can't burn CDs (TDK) on a Dell Computer (with PHILIPS DVD+-RW DVD8801).

I tried both wodim and cdrskin in K3B, but both fail.
Both fail Optimum Power Calibration. Cdrskin continues after OPC fails because of a --force option, but then fails while writing the lead-in (I think).

When using wodim:
```
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 7.718s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:   11.810s
```

When using cdrskin:
```
Executing power calibration...
ERROR: Power calibration failed.
ERROR: Ignored because of option --force.
/usr/bin/cdrdao: Input/output error.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 12 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 61152
cmd finished after 11.304s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.
```

Did anyone get their problems fixed?

(This is a duplicate of posts on thread number 366814).

---

### Post by daradib on 2007-08-22
Entire debug texts.

(Duplicate post on thread number 366814)

---

### Post by daradib on 2007-08-22
Problem appears to be hardware related (CDs or burner) since I can't burn in Windows either.

---

### Post by likemindead on 2007-08-23
Yeah... here's what I get:

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
Vendor_info    : 'MITSUMI '
Identification : 'CR-48X9TE       '
Revision       : '5.0E'
Device seems to be: Philips CDD-522.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1589248 = 1552 KB
FIFO size      : 12582912 = 12288 KB
dSpeed set to 4234 KB/s
 writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 158978
Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.992s timeout 60s
wodim: OPC failed.
Writing  time:   18.501s

```

Help? Uber-Thanks in advance....

---

### Post by likemindead on 2007-08-23
*"Ah do deeclaire, whuteva shall Ah do?!"*

:::Cough--BUMP--Achoo:::

---

### Post by gigaferz on 2007-09-03
me too...

---

### Post by pimpaulogy on 2007-10-03
Has anybody figures out how to fix this yet?

I am getting the same issue too and it's rather frustrating.

---

### Post by unutbu on 2008-07-14
Perhaps the problem is that a /usr/bin/nautilus-cd-burner process is running in the background. 

This morning as I was trying to burn a dvd I got the following error from wodim:

```
out@lunch:~% sudo wodim fs=16m dev=/dev/dvd -dao -v /tmp/dvdimage
...
**Track 01:    0 of  887 MB written.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error**
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 10 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x10 (medium not formatted) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s

write track data: error after 0 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:   18.988s
Average write speed 111.0x.
Fixating...
Fixating time:    0.003s
wodim: fifo had 255 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
```

I happened to notice nautilus-cd-burner in my process list:

```
out@lunch:~% ps axuw
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
...
out      15720  0.7  1.6  38236 17076 ?        S    07:23   0:01 /usr/bin/nautilus-cd-burner
out@lunch:~% kill 15720

```
Upon killing this process, I was successfully able to use wodim again.

---

