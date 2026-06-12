---
title: "cdrecord problems"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2006-10-30
The following error is show after trying to erase a CDRW with GmoneBaker.

My CDR is in IDE 2 as slave. Liteon CDR /dev/hdd

cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
cdrecord: Device or resource busy. Cannot open '/dev/hdd'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by Lapeth on 2006-11-22
I experienced the same problem yesterday, and found the site:

[http://cdrecord.berlios.de/old/private/cdrecord.html]("http://cdrecord.berlios.de/old/private/cdrecord.html")

Apparently the site of the author of cdrecord. There you can download the source and compile it. You need smake for this, the one in the repository works fine, but it may give a lot of warnings. Just run 
```
sudo smake
sudo smake install
```
in the source folder, restart, and it should work (did for me). Apparently cdrecord in the repos is broken?
Also, I ran
```
sudo chmod 777 /dev/sg0
```
but I'm not sure if that's necessary (got the hint from another thread here). Hope it solves your problem.

---

