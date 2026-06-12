---
title: "I've spent day doing my research, I need help now"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by min_max9000 on 2007-02-09
It has been asked over and over again and I have read so many of the posts, and the HOWTO's and searched on google etc... I cannot set my SCREEN RESOLUTION. Can you help? This is the machine I have installed "Edgy" on:

Machine Name:	Power Mac G4
  Machine Model:	PowerMac3,6
  CPU Type:	PowerPC G4  (3.3)
  Number Of CPUs:	1
  CPU Speed:	1.25 GHz
  L2 Cache (per CPU):	256 KB
  L3 Cache (per CPU):	1 MB
  Memory:	2 GB
  Bus Speed:	167 MHz
  Boot ROM Version:	4.4.8f2
  Serial Number:	XxxxxxxxxPC1

and this is the graphics set up:

ATI Radeon 9000 Pro:

  Chipset Model:	ATY,RV250
  Type:	Display
  Bus:	AGP
  Slot:	SLOT-1
  VRAM (Total):	64 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4966
  Revision ID:	0x0001
  ROM Revision:	113-99702-131
  Displays:
Apple Cinema Display:
  Display Type:	LCD
  Resolution:	1680 x 1050
  Depth:	32-bit Color
  Core Image:	Not Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported
Display:
  Status:	No display connected


And this is what I have been able to gleen from various post (the question marks are where I am stuck):

Section "Monitor"
    Identifier      "Apple Cinema Display"
    HorizSync	    28-96
    VertRefresh	    43-60
    Option	    "DPMS"
    Modeline        "1920x1200" 155.0 1920 1984 2016 2144 1200 1203 1206 1212 -HSync +Vsync
EndSection



Section "Device"
    Identifier "agp0"
    Driver     "?????????"
    BusID      "?????????"
EndSection



Section "Screen"
    Identifier   "Default Screen"
    Device       "Card0"
    Monitor      "Apple Cinema Display"
    DefaultDepth 24
    SubSection "Display"
        Depth    24
        Modes    "1920x1200" "1680x1050" "1400x1050"
    EndSubSection
EndSection

Thanks in advance for your help.

---

### Post by taurus on 2007-02-09
For Driver, use **vesa** for now and for the BusID, run this command and see which one is it.

```
lspci
```

---

### Post by min_max9000 on 2007-02-09
Like this?

Driver "vesa"
BusID "0000:00:10.0"

---

### Post by taurus on 2007-02-09
It should look more like

```

BusID     "PCI:1:0:0"

```

---

### Post by min_max9000 on 2007-02-09
OOPPSS!!! I have bunged it now. I tried to go through the whole "Auto detect" configuration... GDM is turned off completely now. EEK! What do I do? Reinstall ubuntu?

---

### Post by -Ghost9- on 2007-02-09
i don't know if this will help, but I recently got my ati card working using the ati drivers by following these instructions:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

---

### Post by min_max9000 on 2007-02-09
Ok, I had to reinstall Edgy. Now I am back to where I started. This is what I get with lspci:

adam@ubuntuagp:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth 2 ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 01)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM)


Can someone please tell me what my BusID would be from this?

---

### Post by taurus on 2007-02-09
Run this command from a prompt and if you are not sure about an answer, just use the default.

```
sudo dpkg-reconfigure xserver-xorg
```
Otherwise, it's 

```
BusID   "PCI:0:0:10"
```

---

### Post by min_max9000 on 2007-02-09
> **taurus said:**
> Run this command from a prompt and if you are not sure about an answer, just use the default.

```
sudo dpkg-reconfigure xserver-xorg
```
Otherwise, it's 

```
BusID   "PCI:0:0:10"
```That's the second time I have gone through that configuration and wound up with GDM turned off and an all black screen. How do I recover from that?

---

### Post by shareMenaPeace on 2007-02-09
When you run sudo dpkg-reconfigure xserver-xorg did you just used the default settings?
And you can try booting in recovery mode and than run 

```
dpkg-reconfigure xserver-xorg
```

---

### Post by min_max9000 on 2007-02-09
how do I boot in recovery mode?

---

### Post by shareMenaPeace on 2007-02-09
Restart the computer(ubuntu -> logout -> retstart) = booting

Than when the GRUB boot loader appears choose recovery mode.

---

### Post by taurus on 2007-02-09
When it first boot, you will see a GRUB screen with a time counting down.  You have three seconds to press the Esc key to see the menu.  That's where you get into the recovery mode.

---

### Post by min_max9000 on 2007-02-09
I don't know about any GRUB screen. All I get is the yaboot loader which allows me to select between linux, os x or cd-rom... I am so lost.

---

### Post by m4sterblast3r on 2007-02-09
when your system just turns on, first thing you see is your bios finding hard drives and stuff, next should be a quick thing that looks just like that, says grub in small text top left of screen for a couple seconds, its pretty quick, then ubuntu logo shows up. so before the ubuntu logo shows up you hit esc

---

### Post by min_max9000 on 2007-02-09
I'm not using GRUB, I am using Yaboot 1.13.1 (or something) and the options I get are:
l: GNU Linux
x: mac os x
c: CD rom
boot:

When I press esc from here, I am taken to another Yaboot prompt that just says "boot:".

---

### Post by shareMenaPeace on 2007-02-09
He uses a power pc those use yaboot - start the yaboot error console

---

### Post by min_max9000 on 2007-02-09
So the next stupid question... how do I start the Yaboot error console?

---

### Post by shareMenaPeace on 2007-02-09
Seems like yaboot don thave such a mode.
All i found was a firmware mode.

Ok i found another thread with some more instructions 
They slightly differ give it a try.

[http://ubuntuforums.org/showthread.php?t=208307](http://ubuntuforums.org/showthread.php?t=208307)

And checkout this forum board for apple user
[http://ubuntuforums.org/forumdisplay.php?f=133](http://ubuntuforums.org/forumdisplay.php?f=133)

---

### Post by min_max9000 on 2007-02-16
This story has a happy ending. I got away from it for a week, reinstalled ubuntu, configured the graphics... I am now viewing my screen at 1680 X 1050! Woohoo! Thanks everyone for your help an patience.

---

