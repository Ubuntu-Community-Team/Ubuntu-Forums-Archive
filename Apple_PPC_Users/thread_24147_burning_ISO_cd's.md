---
title: "burning ISO cd's"
date: 2005-04-05
forum: Apple PPC Users
---

### Post by trash on 2005-04-05
Is there a fix yet? Wanna try out the live cd but can't burn it.
I've seen and tried what is recommended in other threads like enabling DMA but no luck. Are there other programs to burn?

thanks.

---

### Post by DJ_Max on 2005-04-05
[http://ubuntuppc.info/Misc/ISOImage](http://ubuntuppc.info/Misc/ISOImage)

---

### Post by trash on 2005-04-05
great... if ya have osX lol
I did boot into os9 to burn it but I REALLY didn't want to.

---

### Post by skoal on 2005-04-06
I don't know if my old 2.6.x kernel problem is related to yours or not, but here's how I burned an ISO file *without* using 'scsi-ide' emulation or a GUI.

Get the 'cdrtools' and 'cdrdao' packages.
```
cdrecord -v dev=/dev/hdc isoimage.iso
```
* replace 'hdc' with your cdrw device.

Your request must pertain to something else entirely though I assume.  If not, that's how I burnt my Ubuntu ISO.

---

### Post by ceratophyllum on 2005-04-12
Here's how I did it
```

sudo cdrecord dev=IODVDServices hoary-live-powerpc.iso

``` 

I'm running Panther and I installed cdrecord with Fink.

---

### Post by sgmorr on 2005-05-10
Try FireStarter FX.

Steve M.

---

### Post by Ptero-4 on 2005-05-10
[QUOTE=sgmorr]Try FireStarter FX.

Steve M.[/QUOTE]
 Apply the latest combo update to Panther (It fixes the Disk Utility crashes) and burn through disk utility.

---

### Post by trash on 2005-08-01
Thanks for the replies, but i am still having problems burning anything.
I've tried a couple of variations including installing gcdw and what was suggested here...
Here's an output of my last attempt. So whats the story anyway, it worked great in Warty so what happened?

thanks.

sudo cdrecord -v dev=/dev/hdc /home/kenji/MOVIES/Hitchhikers_Guide.avi
Password:
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01a38 (powerpc-unknown-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-powerpc
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX140E  '
Revision       : '1.2a'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 4183808 = 4085 KB
Drive DMA Speed: 3023 kB/s 17x CD 2x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   699 MB
Total size:      803 MB (79:36.53) = 358240 sectors
Lout start:      803 MB (79:38/40) = 358240 sectors
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
Trying to clear drive status.
cdrecord: Drive needs to reload the media to return to proper status.
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 1609
Starting to write CD/DVD at speed 8 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
cdrecord: Success. read track info: scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 12 00 00 00 00 24 00 00 C0
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) error refers to command part, bit ptr 0 (not valid) field ptr 0
resid: 28
cmd finished after 0.001s timeout 240s
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
cdrecord: Cannot get next writable address.
Writing  time:    0.055s
Average write speed 999.0x.
Fixating...
Fixating time:    0.003s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

---

### Post by trash on 2005-08-03
Hmm, I don't know why I always thought Gnomebaker was available for x86 only, but after stumbling across it in the repo's I installed and without any effort at all have been burning cd's all morning! :) ... YAY!

---

