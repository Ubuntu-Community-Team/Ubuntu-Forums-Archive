---
title: "iBook G4 + external monitor"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by perl_user on 2006-06-18
hi,

is it possible to connect from the ibook to a extern monitor?
(dapper inside)

---

### Post by unconquerable on 2006-06-19
I am also curious about this, using the VGA adapter.

---

### Post by blue_chili on 2006-09-14
Hi,

I know this response might be a bit late but if anyone else does the search they should hopefully see this, hoping I can help someone who was in a similar boat to me!

See my post here:
[http://www.ubuntuforums.org/showthread.php?p=1497267#post1497267](http://www.ubuntuforums.org/showthread.php?p=1497267#post1497267)

Read my post first and then the article to get the full instructions.

Make sure you are running dapper (instructions here for upgrading): [http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Dapper#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake))

Cheers,
Olivia

---

### Post by rojak on 2006-10-17
Cool! Thanks, it put me on the right track. Actually it almost worked for me. After some more tweaking, swearing and x number of reboots I got it working using the following xorg.conf:


(relevant section only; BTW no LeftOf / RightOf; just cloning the LCD for presentations)
==========================================================================
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

