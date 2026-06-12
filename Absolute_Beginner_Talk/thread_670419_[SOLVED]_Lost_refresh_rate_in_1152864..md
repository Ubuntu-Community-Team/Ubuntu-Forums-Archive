---
title: "[SOLVED] Lost refresh rate in 1152*864."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-17
I used 1152*864 screen resolution with 70 or 75 refresh rate(can't remember exactly) in windows and in Ubuntu before.
I'm using 1024*768 nowadays.85 refresh rate.
Today i want to go back to 1152*864 but there are only two options in refresh rate 55 and 60.
Why this can happen?
I'm using a CRT monitor so this is important for me.
Thanks anyway.

---

### Post by FuturePilot on 2008-01-17
What is your graphics card?

---

### Post by rhc on 2008-01-17
> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

..

---

### Post by rhc on 2008-01-17
No way?

---

### Post by DeusEx on 2008-01-17
check your /etc/X11/xorg.conf

mine does exactly what you want:

```

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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "ATI Radeon R300"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
        Option          "Composite"     "0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-68
        Vertrefresh     50-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon R300"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1152x864"
        EndSubSection
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

Section "ServerFlags"
        Option          "blank time"    "0"
        Option          "standby time"  "0"
        Option          "suspend time"  "0"
        Option          "off time"      "0"
EndSection


```

you probably only need to change your own sections to the values that resemble mine:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-68
        Vertrefresh     50-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon R300"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1152x864"
        EndSubSection
EndSection

```

PS Always backup before you start modifying!

---

### Post by rhc on 2008-01-18
Worked like a charm DeusEx.
Thanks so much.

---

### Post by BillDozer on 2008-01-18
Please mark the thread as solved.

---

