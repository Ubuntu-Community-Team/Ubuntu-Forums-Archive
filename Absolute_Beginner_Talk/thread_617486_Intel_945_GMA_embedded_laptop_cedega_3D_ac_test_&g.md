---
title: "Intel 945 GMA embedded laptop cedega 3D ac test &gt; EVE onlceleration"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by samdude9 on 2007-11-19
Hi all!

Was about to come back to linux after a long break (long enough to put me back in the newbie section :) ) as the port of eve online to linux had finally been released.

To my dismay, this 'port' was in actual fact a wrapper to cedega for eve. But oh well...

The problem came when I tried the 3D acceleration test in the eve cedega package (the same one from the original cedega) which failed.

I get 860 FPS in glxgears, i try the rendering and (sorry forgot the its name...) 'other' test that people normally tell you to try, they both came out as 'Yes'.

Linux based games work fine and cedega has worked before under... ubuntu 5.10? Somewere in that region regardless.

On the laptop case it says 'Intel 940GML + ICH7-M Supports Intel GMA 950' - But in the windows device manager, it simply says its a... 'Mobile Intel 945GM Express' (My bets with dev manager showing the truth :) )

Im Using ubuntu 7.10 now...

thx
Sam

---

### Post by Seisen on 2007-11-19
Post your xorg.conf file

```
cat /etc/X11/xorg.conf
```

---

### Post by samdude9 on 2007-11-19
Will post xorg.conf in about an hour. (Not at laptop at the moment :()

---

### Post by samdude9 on 2007-11-19
my xorg.conf:

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by codemills on 2008-04-16
> **samdude9 said:**
> my xorg.conf:
........................
.......................
Section "Files"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection
..........
...........
..........

        InputDevice     "Synaptics Touchpad"
EndSection


Even i got Intel driver and cedega 3D accel test FAILS :( . so whats the solution for this?

---

### Post by TheSurak on 2008-05-05
> **codemills said:**
> Even i got Intel driver and cedega 3D accel test FAILS :( . so whats the solution for this?

I'm afraid the only possible solution is asking for Ubuntu guys to develop a decent driver for 945GM. I've contacted Transgaming and they told me that they have no Official Support for 945GM... They also told me that Linux best supports nVidia... So what am I supposed to do? Change my graphics card? Ooops, that can't be done on my notebook... Great... :mad:

---

### Post by samdude9 on 2008-05-13
Thats exactly the hole im in.

The strange thing is, one of the cedega 5.x's worked perfectly for me - but at some point, performance disappeared :(

So, what we gonna do?

I'll set up a petition if you guys want :D lol

Sam

---

### Post by TheSurak on 2008-05-13
> **samdude9 said:**
> Thats exactly the hole im in.

The strange thing is, one of the cedega 5.x's worked perfectly for me - but at some point, performance disappeared :(

So, what we gonna do?

I'll set up a petition if you guys want :D lol

Sam

Please, make it so! :D

I believe you can try older Cedega engines. Things are weirder than we can imagine. It depends on kernel version, xorg version, as far as I can tell. I have a Kurumin Linux (derived from Knoppix, derived from Debian), dist-upgraded to kernel 2.6.22. Cedega works but there are 3D errors with Frozen Throne and I can't eve read text on EVE. In the same notebook, I have a partition with Ubuntu 8.04 LTS, but I can't even run War3 setup on it... Nothing happens...

---

