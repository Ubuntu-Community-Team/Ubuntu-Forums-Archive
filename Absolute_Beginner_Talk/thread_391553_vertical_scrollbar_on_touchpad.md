---
title: "vertical scrollbar on touchpad"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2007-03-23
on windows, the right side on my touchpad acts as a vertical scrollbar

does anyone know how to enable this functionality in kubuntu edgy

toshiba satellite a105 dual bot edgy and xp

---

### Post by ichigo on 2007-03-23
You have to modify your /etc/X11/xorg.conf. I don't have a Toshiba Laptop, but since almost all Laptops have Synaptics touchpads you could try to add (or modify if there already is a section for your touchpad)
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "autodev"
     Option         "LeftEdge" "1700"
    Option         "RightEdge" "5300"
    Option         "TopEdge" "1700"
    Option         "BottomEdge" "4200"
    Option         "FingerLow" "25"
    Option         "FingerHigh" "30"
    Option         "MaxTapTime" "180"
    Option         "MaxTapMove" "220"
    Option         "VertScrollDelta" "100"
    Option         "MinSpeed" "0.06"
    Option         "MaxSpeed" "0.12"
    Option         "AccelFactor" "0.0010"
EndSection

```

These are my settings. They also include horizontal scrolling. If you don't want horizontal scrolling, include the option
   ```
Option         "HorizScrollDelta" "0"
```

Alternatively, you could use the settings from [http://ubuntuforums.org/showthread.php?t=314979](http://ubuntuforums.org/showthread.php?t=314979)

Apply the changes by restarting the X server with Ctrl+Alt+Backspace (all programs with a GUI will be terminated).

---

### Post by sailingboarder on 2007-03-23
it still doesn't work

do i need to remove anything from my xorg.conf file, like an old mouse entry?

---

