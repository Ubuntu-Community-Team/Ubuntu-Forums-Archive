---
title: "Two desktop monitors"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-07-12
I have 2 monitors that work well in Windows XP ... grrrrrrrrrr.
I wonder if it is possible to have it done in Ubuntu Ultimate?
The reason why is that I am learning Flash and Photoshop.
In windows XP  I can have one monitor showing the tut, and the second I can
use it to open my ap. to follow along.
Which is nice .
Any suggestion?
No big deal.... I have a NDVIDIA express  GeForce 7600GT (256 ram )
Oh by the way I like this Linux :guitar:

---

### Post by qamelian on 2007-07-12
Yes, you can do this. There is a tool in the Universe repository called displayconfig-gtk that will help you to setup the two displays. You can search for it in Synaptic or install from the terminal by typing:
```
sudo apt-get install displayconfig-gtk
```

To run it, press Alt-F2 to get the run application box and type:
```
gksu displayconfig-gtk
```

---

### Post by burt_57 on 2007-07-12
Good try man but I must say .......it does not work.....hey could be me.
Oh well will try again. thank.
I have learn something .

---

### Post by Nythain on 2007-07-12
gksudo nvidia-settings from within the terminal and set it up that way, either with twinview (on big desktop stretching across both) or xinerama, depending on your personall preference... i personally didnt use either, i had dual monitors set up running two COMPLETELY different desktops, each with thier own panels, icons, wallpapers, system trays and all that jazz.

play around with it... you could also try googling "linux nvidia dual monitor" or "nvidia dual monitor xorg" to learn how to manually edit your /etc/X11/xorg.conf if you dont want to have nvidia-settings write you a new one (i hated that it just wrote a new one, because it would get rid of all my personall additions)

Here is an example of my xorg.conf for you to go by, keep in mind certain things will be different in yours
```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
    Load           "dri"
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

Section "DRI"
    Mode   0666
EndSection

```
and this is my twinview setup i made because i was bored
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
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

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
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
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +1024+0, CRT-1: 1024x768 +0+0;"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection

```

---

### Post by bodhi.zazen on 2007-07-12
My advice is to:

1. Install the nvidia driver. I have used the same card but have not been able to enable dual monitors with the open source drivers (nvidia-glx-new). If you installed nvidia-glx or nvidia-glx-new you will have to remove them first.

2. Use nvidia settings (as root) to set up your monitors and resolution.

Enter this command in a terminal

```
gksu nvidia-settings
```

Nythain: Yea, I agree. 

FYI: Twinview works quite nicely with XFCE (xfce is much more dual monitor aware then gnome).

With gnome, Right click on a panel -> new panel.

Left click on the new panel -> Hold the left mouse button down and move the mouse to a new location (on the second monitor -> Release mouse button -> viola panel on each monitor ;)

---

### Post by anarchyreigns on 2007-07-13
The easiest way to do it if you have an Nvidia card is to just use Sysinfo. It's located in the repositories. Read this here:
[http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html](http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html)

---

### Post by burt_57 on 2007-07-13
> **Nythain said:**
> gksudo nvidia-settings from within the terminal and set it up that way, either with twinview (on big desktop stretching across both) or xinerama, depending on your personall preference... i personally didnt use either, i had dual monitors set up running two COMPLETELY different desktops, each with thier own panels, icons, wallpapers, system trays and all that jazz.

play around with it... you could also try googling "linux nvidia dual monitor" or "nvidia dual monitor xorg" to learn how to manually edit your /etc/X11/xorg.conf if you dont want to have nvidia-settings write you a new one (i hated that it just wrote a new one, because it would get rid of all my personall additions)

Here is an example of my xorg.conf for you to go by, keep in mind certain things will be different in yours
```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
    Load           "dri"
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

Section "DRI"
    Mode   0666
EndSection

```
and this is my twinview setup i made because i was bored
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
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

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
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
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +1024+0, CRT-1: 1024x768 +0+0;"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection

```

This is what I get

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

And now I get this 

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

---

