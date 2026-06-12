---
title: "Composting Extension Is Not Available."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-10-14
I upgraded my graphics card to a Radion 9550 and also upgraded to Gutsy RC1. Now I get the message that the composting extension is not available. What do I do to fix it?

---

### Post by scwinn on 2007-10-14
Here is more to go on...

sheldon@sheldon-desktop:~$ compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by skompier on 2007-10-14
I have an ATI Radeon 9600 and using LiveCD RC, I get the fading windows effects. Now that I did a complete install of 7.10RC and have the restricted driver enabled, I get the same error as you do, minus the last part. I searched and followed every post on the forums, but no luck.

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

7.10RC found my widescreen monitor and I now have 1440x900, which Feisty had trouble with. I'm not too concerned because everything is working and if I don't have eye-candy, I'm not missing it. I'm more curious to learn why.

In addition...here's my xorg.conf if someone can see any reason.

Section "Files"
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

---

### Post by scwinn on 2007-10-15
It seems that for some unknown reason the Open GL module gets uninstalled when switching to a Radeon graphics card. If this is a Ubuntu bug, how do we post it to the appropriate channels so that it gets resolved?:guitar:

---

### Post by markusf21 on 2007-10-15
[https://bugs.edge.launchpad.net/ubuntu/+filebug](https://bugs.edge.launchpad.net/ubuntu/+filebug)

---

### Post by scwinn on 2007-10-23
Thanks to the forum, this issue is now resolved.

---

