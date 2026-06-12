---
title: "[SOLVED] OpenGL"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by deadfred_10 on 2007-08-07
I installed Kubuntu the other day and nothing  OpenGL works. I know glx for nvida is installed. What is missing?

---

### Post by ukripper on 2007-08-08
What graphics card you are using? and what drivers?

---

### Post by deadfred_10 on 2007-08-08
evga 7800gl and the real nvidia drivers. Never had problems with them on Suse or Mepis. Kubuntu is the only distro that I have needed to jump through hoops to get setup.

---

### Post by asmoore82 on 2007-08-08
did you install the glx drivers via apt/Synaptic or on your own?

EDIT: methinks the question is still valid.

---

### Post by igknighted on 2007-08-08
> **asmoore82 said:**
> did you install the glx drivers via apt/Synaptic/"Restricted Drivers Manager" or on your own?

There is no restricted driver manager in Kubuntu

What is the output of "glxinfo | grep render" on the terminal?

EDIT: The drivers from Ubuntu might be the culprit.  They do not update xorg.conf like most distros, see if that is configured to use the "nvidia" drivers instead of "nv"

---

### Post by deadfred_10 on 2007-08-08
> **igknighted said:**
> There is no restricted driver manager in Kubuntu

What is the output of "glxinfo | grep render" on the terminal?

EDIT: The drivers from Ubuntu might be the culprit.  They do not update xorg.conf like most distros, see if that is configured to use the "nvidia" drivers instead of "nv"

direct rendering: No
OpenGL renderer string: Mesa X11

and glxinfo by itself

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
 

BTW Go Braves! Miss not living up there anymore.

---

### Post by Lord Illidan on 2007-08-08
Give us your /etc/X11/xorg.conf then.

---

### Post by deadfred_10 on 2007-08-08
Section "Device"
  identifier "nVidia Corporation G70 [GeForce 7600 GS]"
  boardname "NVIDIA GeForce 7 Series"
  busid "PCI:1:0:0"
  driver "nv"
  screen 0
  vendorname "NVIDIA"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "ViewSonic"
  modelname "ViewSonic 20"
  HorizSync 30-82
  VertRefresh 50-120
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "nVidia Corporation G70 [GeForce 7600 GS]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1920 1200
    modes "1680x1050@60" "1680x1050@75" "1600x1024@60" "1920x1200@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x720@50" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "1280x854" "1152x768@54" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "720x400@85" "640x350@85" "640x400@85"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "NVIDIA GeForce 7 Series"
  busid "PCI:1:0:0"
  driver "nv"
  screen 1
  vendorname "NVIDIA"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by igknighted on 2007-08-08
As I thought, Ubuntu's drivers do not enable themselves upon install.  You need to enable them by using this command:
```
sudo nvidia-xconfig
```

If that gives you an error, try opening that xorg.conf file and changing "nv" in the device section to nvidia.  Then restart the Xserver (ctrl+alt+backspc).

EDIT: WOAH!!!! delete everything below the EndSection for the DRI section, I'm amazed your xserver starts with all that junk there.

---

### Post by deadfred_10 on 2007-08-08
That did it. This is the first time I used the package manager to install the drivers. In the past I always compiled the kernel and drivers myself.

---

