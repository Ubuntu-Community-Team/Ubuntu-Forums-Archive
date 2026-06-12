---
title: "K3b problems"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-19
I have burned audio disks with K3b before, but now I tried to burn one,and it just froze after about 11%,then tried a RW and it said couldn't erase got this: System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-23-386
Devices
-----------------------
SONY CD-RW  CRX185E3 L08f (/dev/hdc, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

SONY DVD RW DRU-720A JY06 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -tao driveropts=burnfree blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-23-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by gingermark on 2006-07-19
Try running as root - either select to run as root with the entry in the menu editor or launch it with 'kdesu k3b' in KDE or 'gksudo k3b' in GNOME.

Hopefully running k3b as root you won't have the same problems.

---

### Post by MaximB on 2006-07-19
by the way...will k3b work well under gnome ?
or do I have to run it under KDE to work perfect ?

---

### Post by orb9220 on 2006-07-19
When you install any kde app thru synaptic it will install all necessary to run in gnome.

---

### Post by Drakkor on 2006-07-19
I'm running under default Ubuntu with gnome,and it works perfectly ! What happened is I really don't understand the conventions of mounting the CDRoms in /etc/fstab
I used to think that both my CDRW and DVDRW had to be mounted , guess that's not true for them to work. Anyhow since the debug report: Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
I had only /dev/hdd mounted,, so I just put in /dev/hdc, and it worked flawlessly. Go figure ? :D

---

### Post by MaximB on 2006-07-19
> **Drakkor said:**
> I used to think that both my CDRW and DVDRW had to be mounted , guess that's not true for them to work. Anyhow since the debug report: Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
I had only /dev/hdd mounted,, so I just put in /dev/hdc, and it worked flawlessly. Go figure ? :D

that's strange...when I first installed ubuntu it mouted ALL of my drivers including my cd-rw and dvd-+rw...and my 2 hard dirks with 5 partitions..

---

### Post by Drakkor on 2006-07-19
Here's my fstab now;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /windows3       ntfs    nls=utf8,umask=0222        0       0
/dev/hda7       /windows4       ntfs    nls=utf8,umask=0222        0       0

---

