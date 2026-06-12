---
title: "Xinerama == SLOW  ---Please help---"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by JavaIsRobust on 2007-05-27
I setup my quad screen desktop but Xinerama makes things very, very slow.

I want a Quad screen desktop where I can drag windows from window to window and when I maximize a window it only fills up one particular screen instead of more than one screen.  Pretty much the same way Windows would take care of the displays.

Correct me if I'm wrong, but I believe twinview won't work because it's limited to only two displays and when a window is maximized it fills up both displays.  MergedFB won't work cause I'm using Nvidia cards.

My setup...

Dell Dimension 8400
P4 3.6
2gigs ram
X800 PCI-e
FX5200 PCI

18"crt + 22" LCD + 22" LCD + 20" crt
res of (6160 x 1050)

I ended up replacing the X800 with a Nvidia 7300 GS so that I could now have dual Nvidia cards to make things easier.  I hope this was a good choice.

This works perfect for me except for the fact Xinerama makes the computer too slow.

Is there any other way to do this?

I appreciate any help given.

Here is my xorg.conf

[PHP]
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen3"
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    ModelName      "WDE LCM-22w3"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "WDE LCM-22w3"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "DELL M992"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "DELL D1626HT"
    HorizSync       30.0 - 107.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:4:2:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:4:2:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1680x1050 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "metamodes" "CRT-0: 1400x1050 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Videocard3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "metamodes" "CRT-1: 1400x1050 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "false"
EndSection
[/PHP]

---

### Post by JavaIsRobust on 2007-05-27
bump

---

### Post by kc0eks on 2007-12-14
I use two displays and xinerama makes things pretty slow, I have yet to find a solution. So basically, you arent the only one.

---

