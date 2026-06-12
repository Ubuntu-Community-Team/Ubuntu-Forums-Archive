---
title: "What am I doing Wrong"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Woodyballz on 2006-10-28
this is what is says i just want to burn a cd for my new car

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-386
Devices
-----------------------
SONY DVD+-RW DW-D56A PDS7 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R] [Error] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-27-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=8 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-woody/k3b_audio_0_01.inf /tmp/kde-woody/k3b_audio_0_02.inf /tmp/kde-woody/k3b_audio_0_03.inf /tmp/kde-woody/k3b_audio_0_04.inf /tmp/kde-woody/k3b_audio_0_05.inf /tmp/kde-woody/k3b_audio_0_06.inf /tmp/kde-woody/k3b_audio_0_07.inf /tmp/kde-woody/k3b_audio_0_08.inf /tmp/kde-woody/k3b_audio_0_09.inf /tmp/kde-woody/k3b_audio_0_10.inf /tmp/kde-woody/k3b_audio_0_11.inf /tmp/kde-woody/k3b_audio_0_12.inf /tmp/kde-woody/k3b_audio_0_13.inf /tmp/kde-woody/k3b_audio_0_14.inf /tmp/kde-woody/k3b_audio_0_15.inf /tmp/kde-woody/k3b_audio_0_16.inf /tmp/kde-woody/k3b_audio_0_17.inf /tmp/kde-woody/k3b_audio_0_18.inf /tmp/kde-woody/k3b_audio_0_19.inf

---

### Post by timetunnel on 2006-10-28
Try running k3b as root (at least, that solved the problem on my system). Open a terminal and enter:
```
sudo k3b
```
Then enter your root password and do the burning stuff with k3b.

As for the question in the subject line of you post ("What am I doing Wrong"): if you are **more specific** in the subject, it's **very likely** that you get more, earlier and/or better replies. The real answer to a subject like "What am I doing Wrong"  would be "you provided a useless subject" ;) 

If you click on the [Guidlines link]("http://ubuntuforums.org/index.php?page=policy") in the navigation bar of the ubuntu forums, you'll get more information about ways to improve your subject line (especially Section II - Technical Support Policies "When asking for technical support"). It's for your own benefit: you'll get more replies with a good subject. :D

---

### Post by d3v1ant_0n3 on 2006-10-28
In k3b, choose 'Settings'>'k3b setup'.

Put in your password and a new window will open that allows you to set permissions for drives.

I had issues with this with an external dvd writer- this fixed it.

Hope that helps.

---

### Post by jkroto on 2006-12-05
> **Woodyballz said:**
> this is what is says i just want to burn a cd for my new car


```
sudo dpkg-reconfigure cdrecord
```
try this and set as SUID

John

EDIT: for some reason this only worked once, then I had to set up an app launcher for gksudo k3b and/or gnomebaker.

---

