---
title: "24 inch montior low resolution on MacBook Pro"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by kathy4scuba on 2010-05-31
I have installed Karmic Koala 9.10 on both my Mac Mini and my MacBook Pro.  On my Mac Mini, everything works fine and I can get full resolution (1920x1200) of the display. 

When I hook up the same monitor to my MacBook Pro 3,1 (with the Nvidia GeForce 8600M GT graphics card), the highest resolution I can get is 1152x864.  I installed the Nvidia driver using the Synaptic Package Manager.  Most recently, I went to the Nvidia site and downloaded the latest driver (which is newer than what I got with Synaptic).  

To get the monitor working with my Mac Mini, I manually edited the xorg.conf file.  This has not worked for the MacBook Pro.  When I manually set the resolution to 1920x1200, the 24 inch monitor comes up disabled.  Any ideas?

One other piece of info.  I have to use the analog (VGA) input on the monitor because the DVI input of this monitor isn't working.

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400"
EndSection

Section "Screen"
# Removed Option "metamodes" "DFP: 1280x1024 +0+0, CRT: 1920x1080 +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1920x1200_60 +1280+0, DFP: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by linuxopjemac on 2010-06-01
You might want to try 
```
nvidia-settings
```

---

