---
title: "external display for iBook G3 800MHz"
date: 2006-09-29
forum: Apple PPC Users
---

### Post by weiswang on 2006-09-29
I just installed Ubuntu on an iBook G3 800Mhz --- it's so nice. One important thing missing :(  is the external display so I can give presentations with it.

Anyone knows a solution? Thanks a lot!

---

### Post by rojak on 2006-10-17
Been struggling with this for very long.
If it is for presentations then most likely you want to clone the iBook display, rather then LeftOf / RightOf etc. 
Below is the relevant section of xorg.conf that made it work for me on my G4.
Hope it is of any use...

=========================================================================

Section "Device"
  identifier "ATI Technologies, Inc. M11 NV [FireGL Mobility T2e]"
  boardname "ati"
  busid "PCI:0:16:0"
  driver "ati"
  screen 0
  option "MergedFB" "on"
  option "CRT2HSync" "31.0-70.0"
  option "CRT2VRefresh" "50.0-120.0"
EndSection

Section "Monitor"
  identifier "iBook Monitor"
  option "DPMS"
EndSection


Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. M11 NV [FireGL Mobility T2e]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1024 768
#    modes "640x480@60"
#    modes "800x600@72"
    modes "1024x768@70"
  EndSubSection
EndSection

Section "Screen"
  Identifier "iBook Screen"
  Device "ATI Technologies, Inc. M11 NV [FireGL Mobility T2e]"
  Monitor "iBook Monitor"
  DefaultDepth 24
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "iBook Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

---

