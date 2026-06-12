---
title: "Trouble with burning CD"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by No Whammies on 2007-06-22
When I try to burn a CD, I get this error output.  

It allso says K3B has no permission to open the device.  What's going on?


System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-k7
Devices
-----------------------
TSSTcorp DVD+-RW TS-H653A D400 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-28-k7
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
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=4 -dao driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-d*/k3b_audio_0_01.inf /tmp/kde-d*/k3b_audio_0_02.inf /tmp/kde-d*/k3b_audio_0_03.inf /tmp/kde-d*/k3b_audio_0_04.inf /tmp/kde-d*/k3b_audio_0_05.inf /tmp/kde-d*/k3b_audio_0_06.inf /tmp/kde-d*/k3b_audio_0_07.inf /tmp/kde-d*/k3b_audio_0_08.inf /tmp/kde-d*/k3b_audio_0_09.inf /tmp/kde-d*/k3b_audio_0_10.inf /tmp/kde-d*/k3b_audio_0_11.inf /tmp/kde-d*/k3b_audio_0_12.inf /tmp/kde-d*/k3b_audio_0_13.inf /tmp/kde-d*/k3b_audio_0_14.inf /tmp/kde-d*/k3b_audio_0_15.inf /tmp/kde-d*/k3b_audio_0_16.inf /tmp/kde-d*/k3b_audio_0_17.inf /tmp/kde-d*/k3b_audio_0_18.inf /tmp/kde-d*/k3b_audio_0_19.inf /tmp/kde-d*/k3b_audio_0_20.inf

---

### Post by the.phantom on 2007-06-22
i am not a expert !!!

but i did a quick google and the error message dealing with 'sg0"
it seems that is part of scanner software? are you trying to burn something from the scanner?

are you burning a "data cd"
and have the files in a folder?

---

### Post by No Whammies on 2007-06-22
nope.

I'm trying to burn music cds, but this error pops up no matter what program I use.

---

### Post by NeoLithium on 2007-06-22
I'm no expert, but I think you'll have to go into the K3B preferences and manually get it to select your CD drive, I have a feeling that /dev/sg0 isn't your CD burner?  Just a guess on my part.

---

### Post by No Whammies on 2007-06-22
Thanks for the quick responses guys, your spirit is awesome!  I did some search-fu and found the answer (also tested out and passed with flying colors!!).


From:
AdrianoBandeira  
First Cup of Ubuntu
	 	Join Date: Nov 2006
Beans: 1

Re: K3B doesn't start with recording session 
The is on the device /dev/sg0...
Make the following...

[B][I][COLOR="Red"]cd /dev
sudo mv sg0 sg0_old
sudo ln -s cdrom sg0
[/COLOR][/I][/B]

Now you can open the K3B....

Yes I can, Adriano, yes I can!  :-)

---

