---
title: "Burning a cd K3b (permission)"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Lowfront on 2007-01-31
Alright now this is not really making much sense because the other day I burned a dvd project of mine.  But now I'm trying to make a cd and its not working.  I have tried every program there is (I think) and ended up on K3B that I really like.  But of course still doesn't work.

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-generic
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '2,0,0'
scsibus: 2 target: 0 lun: 0
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
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=2,0,0 speed=40 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-lowfront/k3b_audio_0_01.inf /tmp/kde-lowfront/k3b_audio_0_02.inf /tmp/kde-lowfront/k3b_audio_0_03.inf /tmp/kde-lowfront/k3b_audio_0_04.inf /tmp/kde-lowfront/k3b_audio_0_05.inf /tmp/kde-lowfront/k3b_audio_0_06.inf /tmp/kde-lowfront/k3b_audio_0_07.inf /tmp/kde-lowfront/k3b_audio_0_08.inf /tmp/kde-lowfront/k3b_audio_0_09.inf /tmp/kde-lowfront/k3b_audio_0_10.inf /tmp/kde-lowfront/k3b_audio_0_11.inf /tmp/kde-lowfront/k3b_audio_0_12.inf /tmp/kde-lowfront/k3b_audio_0_13.inf /tmp/kde-lowfront/k3b_audio_0_14.inf /tmp/kde-lowfront/k3b_audio_0_15.inf

---

### Post by xopher on 2007-01-31
Just to make sure it's a permissions problem, have you tried burning as root?

I had some problems with k3b and permissions in dapper, a --purge and then reinstall did the trick for me.

---

### Post by Lowfront on 2007-01-31
how would I burn as root?

and how do I do this?

a --purge and then reinstall did the trick for me.

---

### Post by Lowfront on 2007-01-31
?

---

### Post by Lowfront on 2007-01-31
anyone?

---

### Post by buuntuu! on 2007-02-11
had the same problem, here's the answer:
```
gksudo k3b
```
and you run k3b as root

---

### Post by Wynne G Oldman on 2007-06-11
> **buuntuu! said:**
> had the same problem, here's the answer:
```
gksudo k3b
```
and you run k3b as rootThanks for the tip. It worked! I feel like I'm getting somewhere at last. I can now format and burn DVD's with k3b. Is there any way of doing this without running k3b (or any other program that needs to write to my DVD burner) as root through the command line?

---

### Post by Nythain on 2007-06-11
odd that you would have to run k3b as sudo to burn a cd... did you install from repository or tar source???

---

### Post by Wynne G Oldman on 2007-06-11
> **Nythain said:**
> odd that you would have to run k3b as sudo to burn a cd... did you install from repository or tar source???I'm not quite sure what you mean. I've only been using Ubuntu for a week. I installed k3b from  "applications>add remove". I've haven't been able to write to my DVDRW or MP3 player since the initial installation. Every burning program has the same problem, not just k3b. All of these programs tell me that I don't have permission to write to the drive.

---

### Post by Wynne G Oldman on 2007-06-11
> **Wynne G Oldman said:**
> I'm not quite sure what you mean. I've only been using Ubuntu for a week. I installed k3b from  "applications>add remove". I've haven't been able to write to my DVDRW or MP3 player since the initial installation. Every burning program has the same problem, not just k3b. All of these programs tell me that I don't have permission to write to the drive.This is what k3b tells me when it's not run with the sudo command.

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
LITE-ON DVDRW SHM-165P6S MS0R (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Sequential mode detected.
umount: /media/Personal Data, Jun 11, 2007 is not in the fstab (and you are not root)
:-( unable to proceed with format: Device or resource busy

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -blank /dev/scd0 


Gnomebaker gives a similar response.

Any ideas anyone?

---

### Post by Wynne G Oldman on 2007-06-11
> **Wynne G Oldman said:**
> This is what k3b tells me when it's not run with the sudo command.

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
LITE-ON DVDRW SHM-165P6S MS0R (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Sequential mode detected.
umount: /media/Personal Data, Jun 11, 2007 is not in the fstab (and you are not root)
:-( unable to proceed with format: Device or resource busy

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -blank /dev/scd0 


Gnomebaker gives a similar response.

Any ideas anyone?Would it make any difference that I installed with the Wubi installer, which I think means that there are no actual Linux partitions on my HDD, just virtual ones?

---

