---
title: "Crash while burning audio cds!"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by mrrobertbates on 2006-12-31
I've been trying to burn an audio cd but every program I use crashes!  Except for K3b, which gives me an output that looks like this...

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
PHILIPS DVD+-RW SDVD8820 AD15 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-generic
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
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=16 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-robert/k3b_audio_0_01.inf /tmp/kde-robert/k3b_audio_0_02.inf /tmp/kde-robert/k3b_audio_0_03.inf /tmp/kde-robert/k3b_audio_0_04.inf /tmp/kde-robert/k3b_audio_0_05.inf /tmp/kde-robert/k3b_audio_0_06.inf /tmp/kde-robert/k3b_audio_0_07.inf /tmp/kde-robert/k3b_audio_0_08.inf /tmp/kde-robert/k3b_audio_0_09.inf /tmp/kde-robert/k3b_audio_0_10.inf /tmp/kde-robert/k3b_audio_0_11.inf 

The other programs that I have tried are Gnomebaker, Serpentine, and "Disc burning application"(?)  All of them crash either upon moving audio files onto the list of items to burn or upon trying to burn them to cd!  :confused:

---

### Post by jimrz on 2006-12-31
> **mrrobertbates said:**
> I've been trying to burn an audio cd but every program I use crashes!  Except for K3b, which gives me an output that looks like this...

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
PHILIPS DVD+-RW SDVD8820 AD15 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-generic
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
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=16 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-robert/k3b_audio_0_01.inf /tmp/kde-robert/k3b_audio_0_02.inf /tmp/kde-robert/k3b_audio_0_03.inf /tmp/kde-robert/k3b_audio_0_04.inf /tmp/kde-robert/k3b_audio_0_05.inf /tmp/kde-robert/k3b_audio_0_06.inf /tmp/kde-robert/k3b_audio_0_07.inf /tmp/kde-robert/k3b_audio_0_08.inf /tmp/kde-robert/k3b_audio_0_09.inf /tmp/kde-robert/k3b_audio_0_10.inf /tmp/kde-robert/k3b_audio_0_11.inf 

The other programs that I have tried are Gnomebaker, Serpentine, and "Disc burning application"(?)  All of them crash either upon moving audio files onto the list of items to burn or upon trying to burn them to cd!  :confused:

you might try using "brasero" ... if you are running Edgy you can get it via synaptic (you will need to have the universe repo enabled)

---

