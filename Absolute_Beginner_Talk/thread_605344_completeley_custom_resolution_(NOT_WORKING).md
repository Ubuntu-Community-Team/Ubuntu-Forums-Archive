---
title: "completeley custom resolution (NOT WORKING)"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by mouseboyx on 2007-11-06
the list of things that don't work (I have an nvidia card with nvidia drivers (nonfree)):

modelines
the new screens and graphics gui editor for xorg
nvidia-settings.
edited the xorg config file extensively

Xorg:
```

 
Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Boardname    "nv"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "PAVILION M50"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x1024"
    Horizsync    31.5-64.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "PAVILION M50"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    1024
        Modes        "800x600@60"    "1024x768@60"    "800x600@56"    "1280x960@60"    "640x480@60"    "1280x1024@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection
Section "device" #    
    Identifier    "device1"
    Boardname    "nv"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    1
EndSection
Section "screen" #    
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
    SubSection "Display"
        Depth    24
        Modes        "640x480@60"    "640x480@72"    "640x480@75"    "640x480@85"    "800x600@56"    "800x600@72"    "800x600@75"    "800x600@85"    "800x600@60"    "832x624@75"    "1024x768@60"    "1024x768@43"
    EndSubSection
EndSection
Section "monitor" #    
    Identifier    "monitor1"
    Vendorname    "Plug 'n' Play"
    Modelname    "Plug 'n' Play"
Modeline "1024x800@60" 67.92 1024 1056 1312 1344 800 816 824 841
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by markharding557 on 2007-11-07
what is your custom resolution?
do the standard ones work?

---

### Post by mouseboyx on 2007-11-07
My resolution right now is 1024X768

My custom resolution that I wish to achieve is 1024x800

---

### Post by mouseboyx on 2007-11-11
bump

---

