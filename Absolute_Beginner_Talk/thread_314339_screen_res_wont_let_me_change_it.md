---
title: "screen res wont let me change it"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by ThERuLeR on 2006-12-07
so i am new to ubuntu and i have been readingthe forums i dled automatix and installed nvidia drivers but my screen res is still stuck at 640x480 and it wont let me change it to any thing else.

if anyone could thats great thanks in advance.

---

### Post by bodhi.zazen on 2006-12-07
would yo post your /etc/X11/xorg.conf

---

### Post by ThERuLeR on 2006-12-07
> **bodhi.zazen said:**
> would yo post your /etc/X11/xorg.conf

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
 FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
   Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "1772ED"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
    Monitor        "1772ED"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024"
EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

---

### Post by bodhi.zazen on 2006-12-07
Thanks. Two things, first you need to enter you monitor horizontal and vertical settings. You will need to find the information (google), but your monitor section should look like this:

> Section "Monitor"
Identifier "1772ED"
HorizSync 29-121
VertRefresh 50-180
Option "UseEdidFreqs" "true"
Option "DPMS"
EndSection

You will need to find the specs for your monitor however...
 

Next, a small modification to include your desired resoultions.

In the Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
Monitor "1772ED"
DefaultDepth 24
SubSection "Display"

modify the line:> Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection

if 1600x1200 is too much, use> Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection

Then restart X:
Ctrl-Alt-Backspace

Or in a terminal:```
sudo /etc/init.d/gdm restart
```

---

