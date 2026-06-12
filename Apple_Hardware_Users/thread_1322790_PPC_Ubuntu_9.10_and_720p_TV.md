---
title: "PPC Ubuntu 9.10 and 720p TV"
date: 2009-11-11
forum: Apple Hardware Users
---

### Post by cyprien on 2009-11-11
I have 9.10 running on my old PPC Mac Mini and it runs great when it's hooked up to the SD monitor. Being I want it to be a media machine for the TV I went to hook it up to my 720p HD television. 

When it gets to the splash screen the video seems to lock up but the boot music still plays and the computer sounds like it's working just fine. I can put in disc and eject it normally and everything, it just never gets beyond the splash.

I have it hooked up to the TV through the DVI port of the Mini to the VGA port of the TV if that helps.

Any ideas?

---

### Post by cyprien on 2009-11-12
I have read some stuff online saying it could be the video settings in my yaboot.conf file. Could this be the issue? The tutorial I found the info in was for getting Ubuntu on a PS3 so I'm not entirely sure it is a smart idea for me to try.

---

### Post by tiresia on 2009-11-12
Maybe you should try to boot without splash. At the second prompt type 'Linux nosplash'

---

### Post by damienf on 2010-03-04
hi, I've had the same problem and after looking through kernel and Xorg source, I've managed to configure ubuntu to boot straight into S-Video/Composite using the G4 mac mini and the apple S-video/Composite connector:

in yaboot.conf,  change the 'append' line with following:

```
append="quiet nosplash video=radeonfb:1024x768,ignore_edid"
```you will need a custom xorg.conf with following info:

```
Section "ServerLayout"
        Identifier     "X.org Configured"
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
        Load  "record"
        Load  "dri"
        Load  "extmod"
        Load  "glx"
        Load  "dri2"
        Load  "dbe"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Device"
        Identifier  "Radeon"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV280 [Radeon 9200]"
        BusID       "PCI:0:16:0"
        Option      "Monitor-S-video"  "TV"
        Option      "TVStandard"       "pal"
        Option      "ForceTVOut"       "true"
        Option      "EnablePageFlip"   "true"
        Option      "UseFBDev"         "false"
        Option      "ConnectorTable"   "0, 2, 0, 5, 0, 2, 0, 5"
EndSection

Section "Monitor"
    Identifier  "TV"
    Option      "DPMS"      "false"
EndSection

Section "Screen"
        Identifier "TV"
        Device     "Radeon"
        Monitor    "TV"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "800x600"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

```Unfortunately, the stock radeon driver **only** allows 800x600 on TV output.

Enjoy.

---

