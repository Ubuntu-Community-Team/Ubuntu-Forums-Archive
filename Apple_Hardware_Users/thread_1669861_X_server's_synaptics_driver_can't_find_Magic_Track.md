---
title: "X server's synaptics driver can't find Magic Trackpad"
date: 2011-01-18
forum: Apple Hardware Users
---

### Post by ubuntie on 2011-01-18
Hi all,

I'm running Ubuntu on a Dell desktop. I have a USB bluetooth device. The X server can find the Magic Trackpad just fine but it believes that it is a mouse, not a touch pad.

Here's my current xorg.conf:
```

Section "Module"
        Load "synaptics"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option         "SHMConfig" "true"
EndSection

Section "InputClass"
    Identifier "tap-by-default"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option         "SHMConfig" "on"
EndSection

Section "InputDevice"
         Driver "synaptics"
         Identifier "touchpad"
         Option         "TapAndDragGesture"     "true" # Switch on/off the tap-and-drag gesture. The gesture is enabled by default.
         Option         "SHMConfig" "on"
        #MatchUSBID "05ac:030e" <-- causes X to fail to start.
        Option "TapButton1" "1"
Option "Emulate3Buttons" "on"
#Option "TapButton2" "3"
#Option "TapButton3" "2"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E2009W"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300 GE"
         Option         "SHMConfig" "on"
EndSection

```

Can anyone assist?

Here is my logfile:

(II) Synaptics touchpad driver version 1.2.2
touchpad no synaptics event device found
(EE) xf86OpenSerial: No Device specified.
(EE) Synaptics driver unable to open device
(EE) PreInit failed for input device "touchpad"
(II) UnloadModule: "synaptics"

---

