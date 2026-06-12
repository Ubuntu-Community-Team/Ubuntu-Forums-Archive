---
title: "2 problems"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-04-02
1) When I hit the power button in the top right, my only options are "Log out", "Switch User", and "Hibernate"

2) I have my screen saver to start in 1 hour. In 1 hour, the system logs me out, and then just gives a blank screen. Also, when I am in the screensaver settings, the mouse completely freezes and I have to restart using the button on my case.

:confused: I'm getting angry :mad:

---

### Post by bapoumba on 2007-04-02
Are you runing, compiz/beryl xgl and such ?

---

### Post by Gorthus on 2007-04-02
No.. Pretty much default edgy.

---

### Post by Gorthus on 2007-04-03
24-hour bump... Can't anyone help?

---

### Post by bapoumba on 2007-04-04
Have you installed proprietary drivers for you video card? Ati or nvidia, if so ?

---

### Post by freebird54 on 2007-04-04
Don't know if I can help - but something similar sometimes happens with video driver problems.  If you post us some system specifications, as well as what driver(s) you are running it will improve your odds of a fix tremendously!

Other potential useful info would include the output from
```

cat /etc/X11/xorg.conf
```

More when we know more :D

---

### Post by Gorthus on 2007-04-04
I'm using the most recent video drivers:

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "GLcore"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    35.0 - 100.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "Capabilities" "0x00000800"
        Option      "UseFastTLS" "off"
        Option      "KernelModuleParm" "locked-userpages=0"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO
OpenGL version string: 2.0.6400 (8.35.5)

```

---

### Post by freebird54 on 2007-04-05
That all looks pretty good.  What screensaver are you actually running?  I ask because there are some on there (Gleidoscope (sp) for one ) that freeze me too - but I just stay away from them now - Cosmos and other slideshow style ones are fine.

The lack of buttons I have only seen happen with Beryl = and the fix for that appears to be some extra code in the startup file for the session you are running.  I would have to start looking there for more possibilities at this point.  Not haing run into this trouble myself, I don't have the structure of things clearly in mind right now.


Also - unlikely probably - but there *IS* one entry in my xorg,conf that is not present in yours - here is the relevant section from mine (difference in **bold**)

```
Section "Device"
        Identifier  "ATI Radeon 9550"
        Driver      "fglrx"
**        Option      "UseFBDev" "true"**
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection
```

As I don't know the significance of the 'options' in yours yet, I don't know if this would help....

Hopefully an expert will join in on this shortly!

---

### Post by Gorthus on 2007-04-05
Nope, that line didn't help.

I use GMatrix, but now that I got my video card working it's fine.

---

