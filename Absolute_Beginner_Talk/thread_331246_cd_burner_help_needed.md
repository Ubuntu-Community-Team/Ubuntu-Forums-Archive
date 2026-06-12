---
title: "cd burner help needed"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by woodythdog on 2007-01-04
I am attempting to set up a compaq preserio sr1430nx as my primary Umbuntu 6.06 computer I have not been able to get the cd burner to work
The drive does not seem to recognize any media

I have included error logs and system info below any help would be greatly appreciated
[B]
GNOMEBAKER LOG[/B]

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'


FURTHER INFO FROM TERMINAL QUERY
Identifikation : 'CD/DVDW TS-H552B'
Revision       : 'HP08'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Scdrecord: Drive does not support TAO recording.
cdrecord: Illegal write mode for this drive.


FURTHER INFO FROM TERMINAL QUERY

[B]
K3B DEBUGGING OUTPUT[/B]

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices


-----------------------
TSSTcorp CD/DVDW TS-H552B HP08 (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

ASUS CD-S480/A5 0.99 (/dev/hdb, ) at  [CD-ROM] [CD-ROM] [None]
K3b
-----------------------
Size of filesystem calculated: 182

mkisofs
-----------------------
182[B]


FURTHER INFO FROM TERMINAL QUERY[/B]

woody@ubuntu-den:~$ dmesg | grep -i cd | grep -i rom
[17179573.192000] hda: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
[17179573.976000] hdb: ASUS CD-S480/A5, ATAPI CD/DVD-ROM drive
[17179574.040000] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.040000] Uniform CD-ROM driver Revision: 3.20
[17179574.044000] hdb: ATAPI 48X CD-ROM drive, 128kB Cache, UDMA(33)
[17179588.688000] cdrom: open failed.
[17179588.964000] cdrom: open failed.
[17179588.964000] cdrom: open failed.
woody@ubuntu-den:~$
woody@ubuntu-den:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
woody@ubuntu-den:~$

---

### Post by dannyboy79 on 2007-01-04
i had burning issues myself and just went out and bought a new dvd writer with dvd-ram support and decent media and now everything is awesome! but you could give htis a try: [http://ubuntuforums.org/showthread.php?t=217472](http://ubuntuforums.org/showthread.php?t=217472)

by the way, use the search function first before you post threads as most of the issues have already been answered several times in the forums. good luck.

---

### Post by sailor2001 on 2007-01-04
consider k3b as a burner.............google search for that

---

### Post by dannyboy79 on 2007-01-04
that would be pointless! all that's gonna do is install kde dependencies and allow you to have a different gui which uses cdrecord and dvd+rw tools and other command line tools similar to what I have listed. why do you suggest k3B anyway? I use nero linux or just use the command line.

---

### Post by woodythdog on 2007-01-07
thanks for all your imput  
 I have tryed all your tweaks with no luck :(  even nerolinux doesn't see media in this drive
I think the next step for me will be looking for a new dvd burner any more software suggestions? or hardware recomendations.

---

### Post by dannyboy79 on 2007-01-10
I suggest this one, Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive. It's a NEC/SONY product I believe. This drive can burn DVD-RAM as well. Although I haven't used it yet for that. I use TDK DVD+R 16X also. I burn most everything with Nautilus burning engine, also Nero Linux.

---

### Post by MrKlean on 2007-01-10
I use USB mostly now.  I can move it from puter to puter with Ubuntu always seeing it ; )

---

### Post by ComplexNumber on 2007-01-10
> **woodythdog said:**
> thanks for all your imput  
 I have tryed all your tweaks with no luck :(  even nerolinux doesn't see media in this drive
I think the next step for me will be looking for a new dvd burner any more software suggestions? or hardware recomendations.
i suggest that it is because you are are missing various packages. unofrtunately, i don't know the exact one because i don't know what you have installed. but try installing the following to see if it makes a difference:
install libtao-dev, libburn2-dev, burn, and cdrdao.

---

### Post by gus sett on 2007-03-12
this hunch is also to keep trying software 1st before swapping hardware.
for a couple of days, my compaq Vista system couldn't write to its 8X optiarc
DVD drive.  searching on the hardware vendor name brought me to this forum.
HP helped re-enable the write capability.  I then found the read errors to be
caused by another software application, because the TSSTcorp CDW/DVD TS-H492C
drive on my XP system could read the DVD.  Your drive has a higher model number.
More details by searching on _HP optiarc laptop_ if you like.


> **ComplexNumber said:**
> i suggest that it is because you are are missing various packages. unofrtunately, i don't know the exact one because i don't know what you have installed. but try installing the following to see if it makes a difference:
install libtao-dev, libburn2-dev, burn, and cdrdao.

---

