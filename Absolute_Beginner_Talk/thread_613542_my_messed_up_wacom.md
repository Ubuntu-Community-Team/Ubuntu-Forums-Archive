---
title: "my messed up wacom"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Zelix on 2007-11-15
im having a bit of trouble getting my wacom tablet to work.  the stylus works great as a cursor but as soon as i open photoshop the tablet seems to think the stylus end is the eraser and vice-versa.  i dont get any pressure sensitivity either.  ive tried so many fixes.  all end poorly.  i have installed wacom-tools but dont even know if i am supposed to be able to open that and if so... how??  

i even pasted this in the etc/x11/xorg.conf.


Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
  Option        "PressCurve"    "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection


not even sure if the person that posted it meant for us to paste it in there or somewhere else.  

im so lost.  i hope that some of this made sense at all.  any help would be great

thanks for your time.

---

### Post by Zelix on 2007-11-16
no one can help me??

---

