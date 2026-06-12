---
title: "macbook with external monitor at 1440x900"
date: 2007-09-15
forum: Apple Intel Users
---

### Post by albertfc on 2007-09-15
Is it possible to have this configuration with ubuntu? I have a external LCD display and following the instructions of the wiki ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) i can work "only" till 1280x800 on clone mode.

Thanks in advance.

Albert

---

### Post by Meck1982 on 2007-09-18
I think this should be possible. At least I am able to run an external Monitor at 1280x1024 with its native resolution. Search in [this]("http://ubuntuforums.org/showthread.php?t=404686") thread and try it. Good luck!

---

### Post by johndela1 on 2007-09-20
I have a 15 macbook pro and a 30 inch display both at their native res...
here is my X config:
let me know if this works for you
------------------------------------------------------------
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen         "aticonfig-Screen[1]" LeftOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        RgbPath      "/usr/share/X11/rgb"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/TTF"
        FontPath     "/usr/share/fonts/OTF"
        FontPath     "/usr/share/fonts/Type1"
        FontPath     "/usr/share/fonts/misc"
        FontPath     "/usr/share/fonts/75dpi/:unscaled"
EndSection

Section "Module"
        Load  "glx"
        Load  "extmod"
        Load  "xtrap"
        Load  "record"
        Load  "GLcore"
        Load  "dbe"
        Load  "dri"
        Load  "freetype"
        Load  "type1"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
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

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    36.0 - 52.0
        VertRefresh  36.0 - 60.0
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "DefaultRefresh"            # [<bool>]
        #Option     "ModeSetClearScreen"        # [<bool>]
        Identifier  "Card0"
        Driver      "fglrx"
        VendorName  "ATI Technologies Inc"
        BoardName   "M56P [Radeon Mobility X1600]"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth     24
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
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Virtual   2560 1600
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by naraic on 2007-09-20
> **johndela1 said:**
> I have a 15 macbook pro and a 30 inch display both at their native res...
here is my X config:
let me know if this works for you


Sorry if i'm wrong, i'm totally new to the whole GNU/Linux thing, but shouldn't his X.org conf. be totally different to yours since hes using a Macbook with integrated Intel graphics and you have an ATI X1600?

If i'm right, by using your X.org his graphics will just stop working...

---

### Post by johndela1 on 2007-09-28
I'd just change the Driver line to use the driver he currently uses.

I mean this line:

Driver "fglrx"

---

### Post by ivesjd on 2007-10-28
> **johndela1 said:**
> I'd just change the Driver line to use the driver he currently uses.

I mean this line:

Driver "fglrx"

That is just a bad idea.  If anyone else comes across this thread, dont do that.

---

