---
title: "Ubuntu on Gateway Profile"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Shadedwind on 2007-09-22
Whooo! Whoo! It is done!

It took me all day to get the Gateway Profile graphics card set up but I did it!
Yesterday I knew jack about linux.  Today I can actually navigate inside a terminal window.  Beautiful.

So here's what I did.

I went to Gateway's website and found the spec sheet for the computer.

[http://support.gateway.com/support/manlib/Profile/Profile1_5/8505157/05157.htm](http://support.gateway.com/support/manlib/Profile/Profile1_5/8505157/05157.htm)


First I installed Ubuntu 6.06 LTS because of the older Gateway Profile.  

After installing Ubuntu 6.06 I ran in to the same problem as everyone else.  I couldn't get the screen resolution past 640x480.  So the forums came to my rescue.

This Gateway Profile is a cream or beige color Pentium III running at 700 Mhz.  The graphics card is an ATI Rage LT Pro PCI3D.  That really screwed me up.  I kept trying to use the ATI driver, when I should have been using the "i810".


1) I visited this wonderful link.

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

2) I went here next.

[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

3) After I captured the modeline required, and then I went here for a little more help.

[http://ubuntuforums.org/showthread.php?t=83973&page=4](http://ubuntuforums.org/showthread.php?t=83973&page=4)

4) Finally I corrected my biggest mistake.  I stopped trying to use the "ati" driver and instead used the "i810" driver.  After that everything booted just fine and I've got three resolutions to choose from.  

Here is my xorg.conf file.

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
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
    Identifier    "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:1:0"
    VideoRam    4096
EndSection

Section "Monitor"
    Identifier    "Internal LCD"
    Option        "DPMS"
    HorizSync    30-70
    VertRefresh    62-90
    Modeline    "1024x768@62" 63.30 1024 1056 1136 1280 768 768 770 797

EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
    Monitor        "Internal LCD"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600"
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
EndSection

Section "DRI"
    Mode    0666
EndSection


Might I just say that Ubuntu runs faster and smoother than windows ever did on this machine

Although there are still some minor details that need ironing out, it looks great so far.  The wireless card is working great, I'm surfing the web, so I should be able to integrate this into my home network and finally take the next step and install this on my Macintosh.


Oh yeah, one of the websites I used was:
[http://www.linuxcommand.org/lts0050.php](http://www.linuxcommand.org/lts0050.php)

Thanks for everyones help.

You helped breathe life into a machine that was collecting dust.

:)):P=D>:lol::-P:-o

---

### Post by flutti-tutti on 2007-09-22
thanks for taking your time to post this.
A great helping example for me !!

---

