---
title: "xserver refuses to cooperate"
date: 2007-07-29
forum: Apple PPC Users
---

### Post by parithon on 2007-07-29
I've tried searching for a solution in the forums, however the majority of the fixes seem to resolve around using dpkg-reconfigure xserver-xorg.  This doesn't work for me. I still get the error that no display could be found. Any ideas?

I'm currently running feisty 7.04-ppc on an Apple XServer as listed below.

```

processor       : 0
cpu             : 7455, altivec supported
clock           : 999.999997MHz
revision        : 0.1 (pvr 8001 0201)
bogomips        : 66.30
timebase        : 33229489
platform        : PowerMac
machine         : RackMac1,1
motherboard     : RackMac1,1 MacRISC2 MacRISC Power Macintosh
detected as     : 128 (XServe)
pmac flags      : 00000000
L2 cache        : 256K unified
pmac-generation : NewWorld

Linux version 2.6.20-15-powerpc (root@adare) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #3 Sun Apr 15 06:45:49 UTC 2007

```

startx error:
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux xserve 2.6.20-15-powerpc #3 Sun Apr 15 06:45:49 UTC 2007 ppc
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 29 10:54:40 2007
(==) Using config file: "/etc/X11/xorg.conf"

(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

```

xorg.conf snippet:
```

Section "Device"
        Identifier      "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "fbdev"
        BusID           "PCI:1:12:02"
        Option          "UseFBDev"              "true"
EndSection

```

lspci info:
```

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 Ethernet controller: Apple Computer Inc. Tigon3 Gigabit Ethernet NIC (BCM5701) (rev 15)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:0d.0 PCI bridge: Intel Corporation 21154 PCI-to-PCI Bridge
0001:10:11.0 PCI bridge: Intel Corporation 21154 PCI-to-PCI Bridge
0001:10:15.0 RAID bus controller: Promise Technology, Inc. PDC20270 (FastTrak100 LP/TX2/TX4) (rev 02)
0001:10:1b.0 RAID bus controller: Promise Technology, Inc. PDC20270 (FastTrak100 LP/TX2/TX4) (rev 02)
0001:11:07.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:11:08.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:11:09.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:12:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0002:22:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:22:0d.0 Class ff00: Apple Computer Inc. UniNorth 2 ATA/100
0002:22:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 01)
0002:22:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM)

```

---

### Post by pxwpxw on 2007-07-29
What is your xorg.conf Section Monitor.

---

### Post by parithon on 2007-07-29
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by pxwpxw on 2007-07-29
I should say I now 0 about Apple Xserver.

What monitor is it? 
( looking at the Vert and Horiz monitor ranges)
======

Looking at the startx error no device detected more like it, can you just post the whole of /var/log/Xorg.0.log
it might have some problem detecting the video card. 
See below re BusID

=======
Also, have you tried in Section "Device" 
          Driver "radeon"

Maybe "fbdev" is not supported by your RV100  video chip, 

(xorg radeon driver supports your RV100, according to man radeon).

=====BusID another possibility=====

There may be a problem with the BusID for Device, depends how it was generated.

From lspci, where bus id uses hex numbers:

0001:12:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]


But in xorg.conf, which normally uses decimal numbers (in several installations here)

Section "Device"
        Identifier      "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "fbdev"
        BusID           "PCI:1:12:02"
        Option          "UseFBDev"              "true"
EndSection

This would be PCI:1:18:02 in decimal, possibly the full PCI:1:18:02:0 to match the lspci ID.
Cant find anything specific about this, you might try some variations.

---

### Post by 3rdalbum on 2007-07-30
In your Section "Device" (or when you use sudo dpkg-reconfigure xserver-xorg), you should try the "ati" or the "radeon" driver, rather than fbdev.

---

