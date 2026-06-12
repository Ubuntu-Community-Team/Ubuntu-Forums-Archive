---
title: "Setting the primary monitor"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by VII on 2008-02-17
Hello all!

Im trying to setup a dual view config using a monitor with a DVI input and a projector with a VGA input. I want the monitor as primary and the projector as secondary.

I almost got it working, but it seems my projector is acting as primary. The startup screen is displayed on the projector, the taskbar is stretched between the two and so is the login screen.

Anyone know how to fix this??

Here's my xorg.conf:

```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Primary Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "HP Pavilion"
    ModelName      "f1904"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Projector"
    VendorName     "InFocus"
    ModelName      "LP640-A"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    ModeLine       "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine       "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine       "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine       "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Device"
    Identifier     "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Primary Screen"
    Device         "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Monitor"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP, CRT, TV"
    SubSection     "Display"
        Virtual     1400 1050
        Depth       24
        Modes      "640x480@60" "640x480@72" "640x480@75" "640x480@85" "800x600@56" "800x600@72" "800x600@75" "800x600@85" "800x600@60" "832x624@75" "1024x768@85" "1024x768@75" "1024x768@70" "1024x768@60" "1024x768@43" "1152x864@75" "1280x960@60" "1280x1024@60" "1400x1050@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Secondary Screen"
    Device         "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Projector"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1024+0, DFP: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60" "640x480@72" "640x480@75" "640x480@85" "800x600@56" "800x600@72" "800x600@75" "800x600@85" "800x600@60" "832x624@75" "1024x768@85" "1024x768@75" "1024x768@70" "1024x768@60" "1024x768@43" "1152x864@75" "1280x1024@75" "1280x960@60" "1280x960@85" "1280x1024@85" "1280x1024@60" "1280x960@75" "1400x1050@60" "1400x1050@75" "1600x1200@65" "1600x1200@60" "1600x1200@75" "1600x1200@70" "1792x1344@60" "1856x1392@60" "1920x1440@60" "2048x1536@60"
    EndSubSection
EndSection


```

---

### Post by nonewmsgs on 2008-02-17
have you gone to systems - administration - screens and graphics?
they have all kinds of options like that and it is easy to use (i was just in there earlier for a friend).

---

### Post by VII on 2008-02-17
Yes, I've played around with that aswell as nvidias settings UI. I never get a good result. :(

---

### Post by VII on 2008-02-17
Actually, right now there's only one monitor in the hardware section of Monitor and Display, called Plug n Play strangely enough.

---

### Post by nonewmsgs on 2008-02-17
i am sorry, but i have to step aside for someone more knowledgeable to help you...

---

### Post by VII on 2008-02-17
I tried this now, but this has resulted in a black projector screen saying "Signal out of range" and a monitor with the res 800x600.

Please help me. :S

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen          0    "Primary Screen"
    Screen          1    "Secondary Screen" RightOf "Primary Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "HP Pavilion"
    ModelName      "f1904"
EndSection

Section "Monitor"
    Identifier     "Projector"
    VendorName     "InFocus"
    ModelName      "LP640-A"
EndSection

Section "Device"
    Identifier     "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Option         "UseDisplayDevice" "DFP"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Option         "UseDisplayDevice" "CRT"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Primary Screen"
    Device         "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480" "800x600" "1024x768" "1280x960" "1280x1024" "1400x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Secondary Screen"
    Device         "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Projector"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480" "800x600" "1024x768"
    EndSubSection
EndSection

```

---

### Post by VII on 2008-02-17
I actually got it working a little bit better now, but its still quite strange. The login screen and taskbar is on my monitor now as I want it, and the projector is no longer displaying out of range. BUT, the screen on the projectir now has its own taskbar, there shouldnt be any there.

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen          0    "Primary Screen"
    Screen          1    "Secondary Screen" RightOf "Primary Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "HP Pavilion"
    ModelName      "f1904"
EndSection

Section "Monitor"
    Identifier     "Projector"
    VendorName     "InFocus"
    ModelName      "LP640-A"
EndSection

Section "Device"
    Identifier     "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Option         "UseDisplayDevice" "DFP"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Option         "UseDisplayDevice" "CRT"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Primary Screen"
    Device         "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Secondary Screen"
    Device         "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Projector"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection


```

---

### Post by VII on 2008-02-17
WOHOOO! I got it working! :D

I finaly switched 
```

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

```
to
```

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

```

and now it works!

---

