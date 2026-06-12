---
title: "Choppy video on ATI Card (surprise) and Feisty install."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Klainn on 2007-05-09
Recently installed the os and got the ATI video drivers installed and seemingly working correctly (cedega installed and all tests passed fine). When attempting to run video at any resolution (WoW, movie, music video) the video is very choppy like it might be missing frames. I know that's not the case, but that's how I can describe it.

Some ouputs

jason@Gumiho:/var/log$ cat Xorg.0.log | grep "AIGLX"
(==) AIGLX enabled
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

jason@Gumiho:/var/log$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6458 (8.36.5)


jason@Gumiho:/var/log$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7280
01:00.1 Display controller: ATI Technologies Inc Unknown device 72a0
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

Kind of at a loss, not sure where to go from here. Any help or linkbacks appreciated.

---

### Post by Klainn on 2007-05-10
Bump for chance of assistance.

I followed this link to install my ati drivers ...  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Before installing these drivers I had perfect video playback, but low resolution. After the drivers the resolution and colors are as they should be, but video is choppy and unwatchable.

---

### Post by bnuytten on 2007-05-30
> **Klainn said:**
> Bump for chance of assistance.

I followed this link to install my ati drivers ...  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Before installing these drivers I had perfect video playback, but low resolution. After the drivers the resolution and colors are as they should be, but video is choppy and unwatchable.

After installing the drivers, make sure you have them activated... Depending on the method used, it is done automagically. You can check with the following command:
```
glxinfo | grep direct
direct rendering: Yes[
```
If you're using the (default) vesa drivers, you will have choppy playback and the direct rendering will be "No".

I succesfully installed the fglrx drivers, but when watching video (mythtv,totem) the colors are inverted. I think blue is red and vice versa. The green color looks more or less ok. It's kinda funny since all people are blue... Anyway, I think it is a bug with the FGLRX drivers and my X1950pro... Let's hope ATI comes up with a driver update soon [-o<

---

### Post by Klainn on 2007-05-30
Indeed I have checked what you have suggested and all seems to be working fine.

I do get the blue video playback but I can't remember what I have to change to get it, but it's either really choppy or smurf-vision.

Least I'm not the only one.

---

### Post by bnuytten on 2007-05-30
> **Klainn said:**
> Indeed I have checked what you have suggested and all seems to be working fine.

I do get the blue video playback but I can't remember what I have to change to get it, but it's either really choppy or smurf-vision.

Least I'm not the only one.

Yep... either no hardware acceleration (choppy video playback) or smurf vision. Check /etc/X11/xorg.conf. Have a look for the word "vesa" or "fglrx" in the Section "Device".
[LIST]
[*]vesa is some kind of default driver, no hardware acceleration
[*]fglrx, is the official ATI driver (which officially does not support X1950, tv-out and AIGLX as of yet)
[/LIST]

---

### Post by Klainn on 2007-05-30
I do have fglrx as my driver. 

I suppose some day it'll work.

---

### Post by bnuytten on 2007-05-31
> **Klainn said:**
> I do have fglrx as my driver. 

I suppose some day it'll work.

I initially messed up when trying to install the ATI (fglrx) driver from source. I than installed the .deb but for some reason that did not work anymore. The fastest solution was to reinstall Feisty and just install xserver-xorg-fgrlx-driver using aptitude :-)

It is not the latest version and still has the smurf-vision mentioned earlier but it does work. I was hoping the new driver (version 8.36.x I think) had the blue stuff removed and tv-out support. But that may be to much wished for... Didn't succeed to completely install so I do not know if the blue/red bug is fixed. If someone can tell me it is for X1950 based cards, I'll be happy to retry and create a .deb file for anyone's use...

---

### Post by Klainn on 2007-05-31
Last night I tried again, to get the drivers working. No luck, but every post shows you the same steps for getting it working. 

Someday!

---

### Post by bnuytten on 2007-05-31
> **Klainn said:**
> Last night I tried again, to get the drivers working. No luck, but every post shows you the same steps for getting it working. 

Someday!

Let that someday be today (or maybe tomorrow ;)) Here is the driver I have installed. You are using Feisty right?
```

**dpkg --list | grep fglrx**
ii  xorg-driver-fglrx                          7.1.0-8.34.8+2.6.20.5-16.28            Video driver for ATI graphics accelerators
**lsmod | grep fglrx**
fglrx                 540004  11 
agpgart                35400  1 fglrx

```

And my xorg.conf... I commented out the wacom stuff and other than 24 bit resolutions. It seems that fglrx does not support non-24bit anyway so why bother... Oh yes, make a backup of your xorg.conf before you start editing it ;-)
```

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection




Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:8:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1152x864"      "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

---

