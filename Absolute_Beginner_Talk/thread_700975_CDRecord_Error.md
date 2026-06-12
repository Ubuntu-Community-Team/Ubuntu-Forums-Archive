---
title: "CDRecord Error"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2008-02-18
I'm trying to create a multi-session cd using CDRecord, but I'm getting the following error:

john@anothrcomputer:~/kos-checkout/kos/examples/dreamcast/png$ cdrecord dev=0,0,0 -multi -audio audio.raw
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
Device type    : Disk
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ATA     '
Identifikation : 'WDC WD2500JS-60N'
Revision       : '10.0'
Device seems to be: Generic CCS Disk.
cdrecord: Sorry, no CD/DVD/BD-Drive found on this target.


I am usually able to burn CD-Rs with other programs, but CDRecord is giving me trouble. Anyone have an idea?

EDIT: I got it to work. Had to change the device... duh :)

---

### Post by TheLions on 2008-02-20
please mark thread  a solved

---

