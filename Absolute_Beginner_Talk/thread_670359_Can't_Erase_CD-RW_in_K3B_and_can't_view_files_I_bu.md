---
title: "Can't Erase CD-RW in K3B and can't view files I burnt to dvd"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kinson on 2008-01-17
Hi guys, I've recently reformatted back to Dapper (from Gutsy), and I'm having a weird problem.

1) some files I've burnt to my dvd, when I pop the dvd back into my drive, it says I don't have the permissions to view it. Though if I "gksudo nautilus" i can open the dvd as root.

[http://img237.imageshack.us/img237/2114/dvdpermrq0.png]("http://img237.imageshack.us/img237/2114/dvdpermrq0.png")

2) I can't erase cd-rw's, lol !!

here's the debug error from the failure of erasing the cd-rw
```

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-51-386
Devices
-----------------------
ASUS CD-S520/A 2.0K (/dev/hda, ) at  [CD-ROM] [Error] [None]

IMATION IMWDVRW16DLI JSI2 (/dev/hdb, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdb speed=10 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-51-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdb'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM

```

Not sure if it has anything to do with it, but it seems that I've only read access to the cdrom perhaps?
[http://img237.imageshack.us/img237/625/perm2bu0.png]("http://img237.imageshack.us/img237/625/perm2bu0.png")

Really appreciate any help I can get :)

Cheers,
Kinson

---

### Post by kinson on 2008-01-18
Update:

I did an "sudo aptitude purge k3b" and reinstalled it, so far erasing my cd-rw seems ok, will test my dvd burning when I get home later today (am at work now).

Cheers,
Kinson :)

---

