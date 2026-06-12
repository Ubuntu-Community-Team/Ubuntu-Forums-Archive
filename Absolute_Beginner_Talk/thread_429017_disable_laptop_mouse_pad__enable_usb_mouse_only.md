---
title: "disable laptop mouse pad / enable usb mouse only?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by redscheme on 2007-04-30
I'm using a dell inspiron e1505 laptop and i hate using its mouse (i end up touching it every time i type) so i use a usb mouse instead. is there anyway to disable the laptop's mouse pad and use only the usb mouse via ubuntu?

---

### Post by tanguyr on 2007-04-30
Try removing the "Synaptics Touchpad" section in your /etc/X11/xorg.conf file. Be careful! You will need to remove two things:

1) the section that looks like this:
```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "SHMConfig" "on"
EndSection
```

2) and the line 

```
InputDevice    "Synaptics Touchpad"

```

in the section

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

```

---

