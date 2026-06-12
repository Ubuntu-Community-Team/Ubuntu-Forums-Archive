---
title: "Cant burn cd in K3b"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by SteveNorman on 2008-04-08
I tried to burn a music cd using sound juicer and it doesnt seem to read the  cdr correctly. I read where using k3b helps in other posts. I tried it and I get this

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PHILIPS CDD4801 CD-R/RW C1.3 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [Error] [TAO, RAW, RAW/R16]

Compaq DVD-ROM DV-5700B 1.23 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrdao: 1.2.2

cdrdao
-----------------------
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
Using libscg version 'ubuntu-0.8ubuntu1'
/dev/scd1: PHILIPS CDD4801 CD-R/RW Rev: C1.3
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0010)
Starting write at speed 8...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot setup write parameters for session-at-once mode.
ERROR: Please try to use the 'generic-mmc-raw' driver.
ERROR: Writing failed.

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/scd1 --driver generic-mmc:0x00000010 --speed 8 -n -v 2 --force --eject --remote 22 /tmp/kde-steve/k3b_audio_0_.toc 

I pulled the cdr and the dvd player out of an older computer. They both work fine in windows to read and to burn. They are older ide types I think.

I am a linux Noob so any help is welcome

ty, Steve

---

### Post by tango_ninja on 2008-04-08
this is a stab in the dark.......just a guess really, but how did you launch k3b?

right before the errors the output says "no super user permission to..." maybe launching through sudo would solve?

worth a try anyway.

---

### Post by stchman on 2008-04-08
> **SteveNorman said:**
> I tried to burn a music cd using sound juicer and it doesnt seem to read the  cdr correctly. I read where using k3b helps in other posts. I tried it and I get this

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PHILIPS CDD4801 CD-R/RW C1.3 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [Error] [TAO, RAW, RAW/R16]

Compaq DVD-ROM DV-5700B 1.23 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrdao: 1.2.2

cdrdao
-----------------------
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
Using libscg version 'ubuntu-0.8ubuntu1'
/dev/scd1: PHILIPS CDD4801 CD-R/RW Rev: C1.3
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0010)
Starting write at speed 8...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot setup write parameters for session-at-once mode.
ERROR: Please try to use the 'generic-mmc-raw' driver.
ERROR: Writing failed.

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/scd1 --driver generic-mmc:0x00000010 --speed 8 -n -v 2 --force --eject --remote 22 /tmp/kde-steve/k3b_audio_0_.toc 

I pulled the cdr and the dvd player out of an older computer. They both work fine in windows to read and to burn. They are older ide types I think.

I am a linux Noob so any help is welcome

ty, Steve

I don't believe Sound Juicer burns CDs.

To create an audio CD using K3b from MP3s you need another package (libk3b2-mp3).

```
sudo apt-get -y install libk3b2-mp3
```

---

### Post by SteveNorman on 2008-04-08
I launched from apps>sound and video>kb3

I tried to add the other package and got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


not sure how to do what it is asking...

It might not have been sound juicer that I tried before,,but it kept telling me to insert a writable cd in to the tray. I tried both my dvd and my cdr , and different types of cdr disks with the same results. Do I need to configure the disk drives? I used these drives to burn the iso that I used to load gutsy with (burned in windows with no problems as well as several music cds in XP), so I know they do in fact work to burn, and the media works to receive data..

---

### Post by SteveNorman on 2008-04-09
Oh yeah, the songs are in .ogg format

---

### Post by SteveNorman on 2008-04-09
also I have older cd and dvd drives if that gives anyone a clue,,,anyone? drivers or formating needed?

---

