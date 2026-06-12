---
title: "nautilus-cd-burner problems!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Zully Quirke on 2006-08-30
When I try to burn a DVD, it doesn't recognize the fact that I have a DVD-RW in the drive. When I try to burn a CD, it runs through in 30 seconds and says  "Error: Error writing to disc." No detail, that's all. What have I done wrong? :(

---

### Post by edrodgers731 on 2006-08-30
Perhaps try gnome-baker?  I installed it myself before I even tried the stock burner.

Ed

---

### Post by nazgulord on 2006-08-30
I experienced something like this once, and I think I partially or completely solved it by installing/reinstalling some of the packages relating to nautilus cd/dvd burning.

Try some of the packages in post#12 on this thread:

[http://ubuntuforums.org/showthread.php?t=179846&page=2](http://ubuntuforums.org/showthread.php?t=179846&page=2)

This may have been the thread I used...

nazgulord.

---

### Post by Zully Quirke on 2006-08-31
Well, I tried GnomeBaker. here's the output I got when it came back failed:

> cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
cdrecord: Warning: controller returns wrong size for CD capabilities page.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ASUS    '
Identifikation : 'CD-S400/A       '
Revision       : '2.1N'
Device seems to be: Generic mmc CD-ROM.


So basically, it's not recognizing that I have a burner? How do I make it detect the burner aspect of that CD-ROM drive?

---

