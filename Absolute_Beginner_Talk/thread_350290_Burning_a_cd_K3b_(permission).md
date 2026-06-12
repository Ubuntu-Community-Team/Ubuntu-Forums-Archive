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

