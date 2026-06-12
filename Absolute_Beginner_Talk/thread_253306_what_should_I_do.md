---
title: "what should I do?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by piangpha on 2006-09-08
I use Ubuntu 6.06 and want to burn CD?

1)If we want to burn CD, what program should we have to use?

2)Where to download the Program? How to install it? How to burn?

---

### Post by fiver22 on 2006-09-08
Rythmbox (installed by default) burns well for me -try it!

---

### Post by Lord Illidan on 2006-09-08
What do you want to burn?

Audio or Data?

For Data, k3b is by far the best program out there..

```
sudo aptitude install k3b
```

---

### Post by aktiwers on 2006-09-08
Nero also made a linux version. Just google it. :)

---

### Post by leftwing on 2006-09-08
> **Lord Illidan said:**
> What do you want to burn?

Audio or Data?

For Data, k3b is by far the best program out there..

```
sudo aptitude install k3b
```

Yes, K3b is excellent. I used it several times, without any trouble. :)

---

### Post by slacker9876 on 2006-09-08
I too like K3B as it seems to be the most reliable burner I have ever used in the last 10 years. However, when I installed it on Kubuntu 6.06, it tells me "cdrecord does not have permmission to access this device" I am told this can be fixed my K3bSetup2 but you cannot chage the permissions in there. When I set it to group "root" it still fails on the same error.

Any ideas?

I also had to chown my home directory after cp files to it from my smaller drive. Thought this to be odd.

---

### Post by slacker9876 on 2006-09-08
I too like K3B as it seems to be the most reliable burner I have ever used in the last 10 years. However, when I installed it on Kubuntu 6.06, it tells me "cdrecord does not have permmission to access this device" I am told this can be fixed my K3bSetup2 but you cannot chage the permissions in there. When I set it to group "root" it still fails on the same error.

Any ideas?

I also had to chown my home directory after cp files to it from my smaller drive. Thought this to be odd.

```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
HL-DT-ST RW/DVD GCC-4241N A100 (/dev/hdc, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

SONY DVD RW DRU-710A BY01 (/dev/scd0, /dev/sg1) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
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
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
/usr/bin/X11/cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=2,0,0 speed=40 -dao driveropts=burnfree -eject -data /home/chris/Desktop/ubuntu-6.06.1-server-i386.iso 
```

---

### Post by msandersen on 2006-09-08
I don't run KDE, but as far as I remember, K3B setup can be found in the KDE control centre. It should set the permissions as they should be. Not sure if the group is *root*, it may be something like *cdrecord*.

---

