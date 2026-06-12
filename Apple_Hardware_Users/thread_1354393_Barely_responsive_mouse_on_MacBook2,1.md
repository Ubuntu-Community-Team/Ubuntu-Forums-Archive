---
title: "Barely responsive mouse on MacBook2,1"
date: 2009-12-13
forum: Apple Hardware Users
---

### Post by Tralce on 2009-12-13
I just installed Ubuntu 9.10 on a friend's MacBook and the touchpad is barely responsive, as if the sensitivity was set to the lowest level. This was never an issue on OS X 10.5, and it's not an issue on my MacBook2,1 with Ubuntu 9.10. This leads me to believe it's a hardware-specific issue. Is there any way I can compensate for this and tweak the sensitivity manually? It's already at the highest possible level in the mouse settings in Gnome.

---

### Post by linuxopjemac on 2009-12-14
install gsynaptics and tweak it from there.

---

### Post by Tralce on 2009-12-14
I've installed gsynaptics, but it offers an error: GSynaptics couldn't initialize. You have to set SHMConfig true in xorg.conf to use GSynaptics.

Here's the thing. There is no xorg.conf. Is this something new in 9.10 I wasn't previously aware of? How do I set SHMConfig to true if none such a file exists on this computer?

---

### Post by linuxopjemac on 2009-12-14
```
sudo nano /etc/X11/xorg.conf
```

then add the following lines
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "SHMConfig"             "true"
        Option          "MaxTapTime"            "0"
        Option          "HorizScrollDelta"      "0"
        Option          "VertScrollDelta"       "30"
        Option          "TapButton1"            "0"
        Option          "TapButton2"            "0"
        Option          "TapButton3"            "0"
EndSection



```

---

### Post by linuxopjemac on 2009-12-14
from [http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)

---

### Post by Tralce on 2009-12-14
Excellent! Thank you sir. That takes care of my issue famously.

---

