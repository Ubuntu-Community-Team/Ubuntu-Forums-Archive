---
title: "Display problems on Dell Craptop w/ ATI M4"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by gnoel on 2007-07-18
I was given an old 900 mHz Dell Inspiron 8000 laptop loaded with Windoze 2000.  After verifying that the machine worked (at 1280x1024), I immediately set about installing Ubuntu.

After booting from the disk, the display is chopped into three vertical sections.  My active window is visible in the left portion, while the middle and right portion show the default beige desktop with a slice of my active window in between.  I can access the Applications and Places menus, but the System menu options disappear into the center of the screen.

I managed to install Edgy, even though I could only partially read the startup questions.  It booted with the same problem.  I edited xorg.conf to change the screen resolution to 1024x768 instead of 1400x1000 to no effect.  I allowed all update packages to install and rebooted - same problem.  Adding the refresh rates to the monitor section of xorg.conf improved the usable area from 1/3 to 1/2 of the screen such that I can now access the System menu.  The driver for the Video is "ati".

I'm wondering if this might be a RAM issue.  Although my brother (not a computer whiz) said the machine had only 128MB, the BIOS setup screen shows 256MB.  Shouldn't this be enough?  The Video Controller is an ATI M4 with 32 MB.  Is this 32 MB taking away too much RAM for Gnome, or is it insufficient?

Any idea of my next move?  The entire xorg.conf is copied below in case that helps.  Thanks in advance for your attention to my problem!

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
<snip comments>

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    FontPath    "/usr/share/fonts/X11/misc"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
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
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Rage Mobility M4 AGP"
    Driver        "ati"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
        HorizSync       30.0 - 100.0
        VertRefresh     40.0 - 110.0
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Rage Mobility M4 AGP"
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
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection



---

### Post by w4ett on 2007-07-18
Just for testing, boot from the feisty live cd, press F4  (VGA) from the boot screen, set the boot resolution to 800x600 and see if you get a full screen display.

I'm thinking it's a problem with the refresh rates tho.....you might need to dig up the documentation on the laptop display

---

### Post by gnoel on 2007-07-18
Thanks - I think you're on to something.  I think there's even more - searching other forum areas, I found this thread which discusses refresh rates, screen resolutions, and other tweaks for this machine:

[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

I'll try it out tomorrow.

---

