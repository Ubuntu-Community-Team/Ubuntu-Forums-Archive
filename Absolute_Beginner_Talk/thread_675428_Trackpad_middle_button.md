---
title: "Trackpad middle button"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by xRes on 2008-01-22
My laptop how one of these middle button controls for moving the window left right up and down but at the moment mine simply goes down when i press up and the other buttons doent work at all! :0

Any ideas or links much appreciated!
Thanks
xRes

---

### Post by neurostu on 2008-02-27
I have a thinkpad t61, that also has a middle mouse button, I edited my xorg.conf file  and made my "configured Mouse" section look like the one below. That added the behavior you described!  good luck,  remember to back up xorg.conf before you edit it.

```

#Trackpoint
Section "InputDevice"
  Identifier	"Configured Mouse"
  Driver	"mouse"
  Option	"CorePointer"
  Option        "Device" "/dev/input/mice"
  Option	"Protocol"	     "ImPS/2"
  Option	"ZAxisMapping"	     "4 5"
  Option	"Emulate3Buttons"    "true"
  Option	"EmulateWheel"	     "on"
  Option	"EmulateWheelButton" "2"
  Option	"YAxisMapping" 	     "4 5"
  Option	"XAxisMapping"	     "6 7"
EndSection

```

---

