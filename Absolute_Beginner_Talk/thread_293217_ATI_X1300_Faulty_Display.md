---
title: "ATI X1300 Faulty Display"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-04
Whenever I add this to my config file...

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

I get a weird display. It's hard to explain, but it's distorted and unable to be worked with. 
If you minimize and maximize, you can see the contents again, but as soon as you scroll, 
it messes it up again.

If I take the above section out of the xorg.conf, I get a great display but with direct 
rendering off and the wrong driver info on fglrx info.

Please help me get my card working properly. Thank you

---

### Post by shanepardue on 2006-11-05
Is this how all ATI cards work with Ubuntu? I've always worked with Nvidia
and never had a problem, but this is my first encounter with ATI.

Please help!

---

### Post by umpalumap1985 on 2006-11-05
I have an ATI x1300 myself. . .here is a great resource on how to properly configure your fglrx driver. . .
[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

---

### Post by WalmartSniperLX on 2006-11-05
First off I would like to say Im very sorry for posting here since I do not know how to fix your problem. But, as a X1600pro user I can fill you in about ati/linux. Their support with the X1K cards is just horrible. I rip out better performance with my 9200mobile than my desktop. In general ATI's x1k has bad driver support, acceleration, and overall performance is buggy in linux.

I hope that just gives you an idea. Also my ati driver likes to crash my pc when rebooting or shutting down. Some sort of xserver/fglrx/x1k problem I guess. I did some research and found a workaround, but didnt work for me. 

:D

---

### Post by shasta12345 on 2006-11-05
h

---

### Post by shanepardue on 2006-11-06
I followed the thread you provided and I'm still having problems.
Now it's not broken, but it's showing mesa in the fglrxinfo and
there's no direct rendering. Here is my xorg.conf. Thanks for
your patience!

```
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
    Load    "bitmap"
    Load    "ddc" 
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe" 
    Load    "GLcore"
    # Load "extmod" but omit DGA extension
      # (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga" 
  EndSubSection
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
    Identifier    "Generic Video Card"
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
    Option        "UseFBDev"        "true" 
    Option "DRI" "true"
    Option "ColorTiling" "on"
    Option "EnablePageFlip" "true"
    Option "AccelMethod" "EXA"
    Option "XAANoOffscreenPixmaps" 
    Option "RenderAccel" "true"
    #Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
    Option "AGPFastWrite" "on"
    Option          "TripleBuffer" "true" 
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-70
    VertRefresh    50-160
EndSection

Section "Screen" 
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1 
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "640x480" 
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display" 
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480" 
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480"
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

```

---

### Post by shanepardue on 2006-11-06
If I need to supply more information, let me know!

---

### Post by shanepardue on 2006-11-08
Does anyone know if this video card is even able to get XGL or 
AIGLX? It doesn't seem likely from the responses here and the 
extent of tweaking that's been done.

---

