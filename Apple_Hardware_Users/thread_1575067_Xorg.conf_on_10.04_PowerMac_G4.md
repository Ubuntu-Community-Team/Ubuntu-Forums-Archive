---
title: "Xorg.conf on 10.04 PowerMac G4?"
date: 2010-09-15
forum: Apple Hardware Users
---

### Post by downindm on 2010-09-15
I have a fresh install of Lucid on my PowerMac G4 Desktop (PowerMac3,6) / 867MHz.  Right now I'm stuck with a resolution of 800x600.  From what I have read, I know I need an xorg.conf file (install doesn't create one).  I've looked around for a working one - and tried creating my own with no luck.  Perhaps someone can help?  I gather the following information is needed:

```
  *-display               
       description: VGA compatible controller
       product: NV17 [GeForce4 MX 420]
       vendor: nVidia Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list rom
       configuration: driver=nouveau latency=248 maxlatency=1 mingnt=5
       resources: irq:48 memory:91000000-91ffffff memory:98000000-9fffffff(prefetchable) memory:f1000000-f107ffff(prefetchable) memory:90000000-9001ffff(prefetchable)
``````
downindm@dtnet162-61:~$ cvt 1600 1024 76
# 1600x1024 75.90 Hz (CVT) hsync: 81.37 kHz; pclk: 175.75 MHz
Modeline "1600x1024_76.00"  175.75  1600 1712 1880 2160  1024 1027 1037 1072 -hsync +vsync

downindm@dtnet162-61:~$ cvt 1400 1050
# 1400x1050 59.98 Hz (CVT 1.47M3) hsync: 65.32 kHz; pclk: 121.75 MHz
Modeline "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync

downindm@dtnet162-61:~$ cvt 1280 768
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

downindm@dtnet162-61:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

downindm@dtnet162-61:~$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

downindm@dtnet162-61:~$ cvt 640 480
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
```

---

### Post by downindm on 2010-09-15
Got it working... However, I can't seem to get my 1600x1024@76 working properly (the monitor supports that resolution because I am able to select it under OS x.  At any rate, this is what got me working:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dri"
    Load  "glx"
    Load  "dbe"
    Load  "dri2"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
        VendorName   "NEC MultiSync"
        ModelName    "EA222WMe"
        Option       "DPMS"
        HorizSync       31.5-82.3
        VertRefresh     56.0-75.0
        Modeline "1600x1024_76.00"  175.75  1600 1712 1880 2160  1024 1027 1037 1072 -hsync +vsync
        Modeline "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync
        Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
        Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
        Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
        Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    VendorName  "nVidia Corporation"
    BoardName   "NV17 [GeForce4 MX 420]"
    BusID       "PCI:0:16:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
                Modes "1400x1050" "1280x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Note, I did remove the "1600x1024" from the Modes line above because it didn't seem to work.

---

