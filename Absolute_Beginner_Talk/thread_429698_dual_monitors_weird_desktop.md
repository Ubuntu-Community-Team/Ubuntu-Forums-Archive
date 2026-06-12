---
title: "dual monitors weird desktop"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-05-01
ok, im gonna shoot for a quick shot of help in here.

First, my info:
pentium4 2.0ghz with 768mb of DDR with a nVidia Geforce FX5200 Main Monitor is a standard CRT 19' and the next monitor is an old CRT 17' I found lying around.

Next the history:
I decided i didnt want twinview for my dual monitor needs...so i used nvidia-settings and went with a xinerama approach. Had two screens, all that fun jazz, but i encounterd problems. I couldnt decide wich monitor apps loaded on, no big deal except for yakuake. The other problem was, if i watched a movie on one and did anything on the other, they would both get very choppy and laggy.

So i open up my xorg.conf and turn off xinerama. This fixes every problem i HAD, and does EXACTLY what i want it to do... but now i have new problems... so on to them.

Now the Problem:
KDE is drawing my two xinerama screens on top of the screen on my main monitor. Let me try to explain. My background is drawing the wallpaper selected on screen0 from my old xinerama setup, then its drawing the wallpaper from screen1 of my old xinerama setup on top of that, both of wich are being drawn on top of my current wallpaper on my main monitor.
My other monitor is now behaving exactly perfectly, allowing me to set its wallpaper, configure its panels, running completely independent of the main monitor... wich is what i wanted it to do.

Finally the possible Solutions:
Im under the impression now that kde at some point wrote the configuration from when i was running xinerama somewhere. Now that im not running it, its still using all that configuring for just one screen. I just dont know where KDE keeps all its info about what background goes on what screen and all that jazz.

Last but not least the Configs and Screenshots:
here's my current xorg.conf - 
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "STAC Electronics KDS VS-70"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          0
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
    Option         "NoPowerConnectorCheck"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          1
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
    Option         "NoPowerConnectorCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection

```
also the screenshots - 
The first is of the main monitor, keep in mind neither of those two images is what i have my current wallpaper set as, the smaller one in the upper left corner is the original wallpaper of the second monitor (its smaller cause of lower resolution) and then the second one that takes up the whole desktop is the original wallpaper from the main monitor, both were set yesterday while i was running xinerama and have since been changed.
The second screenshot is of my curren second monitor, and its exactly how it should look.

---

### Post by Nythain on 2007-05-01
bump... anyone??? i would hate to have to reformat my machine and get everything set again just to fix a problem that has a solution

---

### Post by zaf on 2007-05-02
Why not use TwinView? It works.

---

