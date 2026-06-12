---
title: "Question about XORG.CONF"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-04-23
ok heres the problem.
i want to make a myth box out of my laptop... and it has an Intel chip... however can not support dual monitors. i want to know if there is a way to output just to the external vga port instead of the laptop screen.  

here is my xorg.conf file:

> Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x- ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
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
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "i810"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

---

### Post by ericmarceau on 2007-04-24
I be blunt:  I don't know the details.

However, I do know at least the following.

1) The xorg.conf file only allows ONE ServerLayout section.

For what you are asking (ability to have to modes of operation, one with notebook screen, the other with external display), there is no simple approach.  It boils down to creating a mode-specific version of the xorg.conf, one for each mode, give each a unique name (i.e. xorg.conf_EXT and xorg.conf_INT) and have a mechanism to prompt at boot as to the choice you wish to use before the OS needs to commit to a mode.

You will need a guru for that, most definitely.


2) You made comment about dual mode (dual-head?).

Since I have an interest in pursuing a dual-head (CAD/CAM) installation, I researched this a lot, but did not finalize anything conclusive.  HOWEVER, I did load up my xorg.conf file with all the parameters and sections that might be needed for when I get around to it.  Also, so that updates don't clobber my definitions, I changed my labels for various sections to custom labels, so that any massaging by installs will only ADD new sections, not replace sections I worked hard at finalizing.

You will find references to a "Dual-Head Setup" in the attached copy of my xorg.conf  .
It might give you hints for researching further, if you did want the dual-head setup.


Eric

---

### Post by adt41287 on 2007-04-24
> **ericmarceau said:**
> 1) The xorg.conf file only allows ONE ServerLayout section.

For what you are asking (ability to have to modes of operation, one with notebook screen, the other with external display), there is no simple approach.  It boils down to creating a mode-specific version of the xorg.conf, one for each mode, give each a unique name (i.e. xorg.conf_EXT and xorg.conf_INT) and have a mechanism to prompt at boot as to the choice you wish to use before the OS needs to commit to a mode.

You will need a guru for that, most definitely.

[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)
I have used this thread to help me to try to get laptop monitor and external monitor both working at the same time.  I however recieved some errors i had searched the errors and came to the conclusions that modifying the xorg.conf to support dual monitor mode was not supported by the Intel 915 chip.  I am trying to output to a tv but was first trying to get it to work on a computer monitor.  Any other suggestions?? i have search thoroughly and dont know what to do next

---

