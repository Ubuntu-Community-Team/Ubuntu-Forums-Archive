---
title: "Upgrade dapper to edgy - no cd burner"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by felin on 2007-04-10
Hi,

I was very pleased wityh myself having upgraded from dapper to edgy and wireless etc working fine - but when I use gnomebaker and other programmes to burn cd they don't work and i get this? Could anyone help ? please
> cdrecord: Warning: Running on Linux-2.6.17-11-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

1 - I have looked for folder called /dev/sg0 and cant find it
2 - have read other forums but none have this problem
3 - can read cds and dvds but not burn

Thanks if you can help me?

> cdrom UNCLAIMED
description: 	SCSI CD-ROM
product: 	DVDRAM GMA-4082N
vendor: 	HL-DT-ST
physical id: 	1
bus info: 	scsi@1:0.0.0
version: 	HA01
capabilities: 	removable
configuration:	
ansiversion	=	5

---

### Post by alexlex on 2007-04-10
it sounds like the dvd drive for some reason is mounted as -r -o it needs to be mounted as -r -w. although i am not sure how to do this. i hope this helped a little

---

### Post by felin on 2007-04-11
> **alexlex said:**
> it sounds like the dvd drive for some reason is mounted as -r -o it needs to be mounted as -r -w. although i am not sure how to do this. i hope this helped a little


Thanks - is anyone able to recommend how to do this?

Should I change to Linux-2.4 and how would I do this?

---

### Post by tgone on 2007-04-11
I'm having the exact same problem. Although the issue started about a month after I upgraded to Edgy.

Does anyone have a solution?

---

### Post by tgone on 2007-04-12
bump.

I still haven't found a solution. Anyone?

---

### Post by felin on 2007-04-12
Is this progress or a step back?? It is strange that I have updated to a linux kerenel that cannot burn cd's!

Have tried the following advice found here: [https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/23203](https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/23203)

> gksu gedit /etc/udev/rules.d/15-local.rules

Paste the following into this file and save:
# SCSI devices
BUS=="scsi", KERNEL=="sg[0-9]", NAME="%k", GROUP="cdrom"

then did

sudo chmod 4755 /usr/bin/cdrecord
sudo chmod 4755 /usr/bin/cdrecord.mmap
sudo chmod 4755 /usr/bin/X11/cdrecord.mmap
sudo chmod 4755 /usr/bin/cdrdao
sudo chmod 4755 /usr/bin/X11/cdrdao


I now get the following when trying to burn with gnomebaker (have also tried kb3):

> cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-11-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GMA-4082N'
Revision       : 'HA01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x0012 
Profile: 0x0011 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x001A 
Profile: 0x001B 
Profile: 0x002B 
Profile: 0x0010 
Profile: 0x0009 (current)
Profile: 0x000A 
Profile: 0x0008 
Profile: 0x0002 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13755 kB/s 78x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
                4 seconds.                3 seconds.                2 seconds.                1 seconds.                0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 9B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.016s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 317440 bytes
Writing  time:   17.483s
Average write speed   2.5x.
Fixating...
Fixating time:   28.670s
cdrecord: fifo had 69 puts and 6 gets.
cdrecord: fifo was 0 times empty and 2 times full, min fill was 93%.

Anybody? Please

---

### Post by dstew on 2007-04-12
The error messages from cdrecord say it looks like a buffer underrun. This can happen when transfer from the hard disk to the memory buffer is slow, perhaps because of a disk problem, or that DMA (direct memory access) is not enabled for the disk, or not working properly. I don't know a lot about DMA, but I know that BIOSes usually have some DMA settings that can be changed. Maybe you could look at that. Also, I think the kernel has DMA services that can be configured. I recall that **nodma** is a boot option. Of course, in your case you want DMA to work, so at a minimum you should check your kernel line in /boot/grub/menu.lst and make sure that it does not disable DMA.

---

### Post by felin on 2007-04-12
> **dstew said:**
> The error messages from cdrecord say it looks like a buffer underrun. This can happen when transfer from the hard disk to the memory buffer is slow, perhaps because of a disk problem, or that DMA (direct memory access) is not enabled for the disk, or not working properly. I don't know a lot about DMA, but I know that BIOSes usually have some DMA settings that can be changed. Maybe you could look at that. Also, I think the kernel has DMA services that can be configured. I recall that **nodma** is a boot option. Of course, in your case you want DMA to work, so at a minimum you should check your kernel line in /boot/grub/menu.lst and make sure that it does not disable DMA.

Thanks for the advice - no luck there. Fail to see anything in BIOS, and no reference in /boot/grub/menu.lst

Anyway - I can still use nautilus desktop burn with "no frills" and am satisfied with that for now, and I still LOVE ubuntu!:D

---

### Post by LaurelLynn on 2007-04-12
GnomeBaker and most burning software defaults to the fastest speed. But has an option to turn it down to something lower.  That often cures buffer underruns.

Note that even if the drive can run at say x16, the disk may say x8.  Sometimes the maker gets optimistic, and a disk that says x32 won´t even burn at x16.  Bigger numbers sell so they tend towards optimism.

---

