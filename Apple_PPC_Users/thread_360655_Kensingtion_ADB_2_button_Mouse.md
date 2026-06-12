---
title: "Kensingtion ADB 2 button Mouse"
date: 2007-02-13
forum: Apple PPC Users
---

### Post by Pottman on 2007-02-13
I'm currently running Ubuntu 6.1 on g3 wallstreet old stype powerbook. I have an external adb kensington 2 button mouse. Whilst the mouse does work, the right hand button simply emulates aleft click.

Anyone have any ideas on how to make the right button emulate a right button click.

I assume it's something to do with buttons and zaxismapping in the xorg.conf but not sure what these should be? Current settings are:

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons "true"
End Section

Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "HorizScrollDelta" "0"
End Section

---

