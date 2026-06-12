---
title: "Iso"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by flaak_monkey on 2006-05-17
I want to burn Ubuntu ISO to a DvD-R (cause i am out of CD-Rs) but K3B wont let me for some reason.  Why is that? I thought you could burn data to a DvD-R the same as a CR-R.:confused:

---

### Post by John.Michael.Kane on 2006-05-17
When you open k3b choose burn dvd iso, and just pick the iso you want to use. i have burned a cd.iso to dvd, and that how it worked when i did it.

---

### Post by Engnome on 2006-05-17
I have written cd isos to cd. So it should work. But that was in windows. I have tried it in gnomebaker, first it said wrong media but later I managed to get it working somehow.

Edit: I think SD-Plisskens method wa the one I used in gnomebaker...

---

### Post by flaak_monkey on 2006-05-17
Cool, that worked Plissken. Thx. (BTW, that movie rocked :P)

---

### Post by John.Michael.Kane on 2006-05-17
You welcome flaak_monkey. gald it worked.

---

### Post by flaak_monkey on 2006-05-20
now i cannot burn ISO in Ubuntu with GNOMEBaker or K3B. Why is this?

---

### Post by user1397 on 2006-05-20
what hapened recently? did you change something?

---

### Post by flaak_monkey on 2006-05-20
[http://img.photobucket.com/albums/v639/axelrose223/Screenshot.png](http://img.photobucket.com/albums/v639/axelrose223/Screenshot.png)

---

### Post by user1397 on 2006-05-20
what permissions are checked in the iso file's properties->permissions tab? (right-click, properties, permissions)

---

### Post by flaak_monkey on 2006-05-20
!st and 3rd row are all checked. The Group one is not though.

[http://img.photobucket.com/albums/v639/axelrose223/Screenshot-1.png](http://img.photobucket.com/albums/v639/axelrose223/Screenshot-1.png)

---

### Post by user1397 on 2006-05-20
iso's are supposed to have these permissions:
Owner: Read and write
Group: Read
Others: Read
and that's it

---

### Post by flaak_monkey on 2006-05-20
the ISO has those permissions but K3B still wont write it for some reason. How do you use (or get to ) K3B setup2?

---

### Post by user1397 on 2006-05-20
[quote=flaak_monkey]the ISO has those permissions but K3B still wont write it for some reason. How do you use (or get to ) K3B setup2?[/quote]
i have no clue! srry i can't help you any longer! :???:

---

### Post by flaak_monkey on 2006-05-21
System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version: 3.3.4
Kernel: 2.6.12-9-386
Devices
-----------------------
MATSHITA DVD-RAM UJ-841S 1.50 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
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
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by cvmostert on 2006-05-21
Try to run k3b as root... 

I am in windows now and want to burn a cd.iso to a dvd disk. windows does not want to do it. I want to burn my breezy cd.iso to dvd because my laptop has problems reading cd, but reads dvd just fine. The cd/dvd drive is on its way out, but I still want to install UBUNTU.

meanwhile i am downloading the ubuntu-install-dvd.iso which takes time...

any help will be great.

Ciao

---

### Post by Ecthelion on 2006-05-21
Have you tried the normal K3B setup?
Settings > K3b setup
There you can change the permission of your writer... 'Cauz maybe that's where the problem is.
There is also a button there to restore the defaults...

---

