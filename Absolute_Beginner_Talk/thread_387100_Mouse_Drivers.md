---
title: "Mouse Drivers?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Gauvenator on 2007-03-17
I have a Logitech G7 Wireless laser mouse that uses USB, and does not work with Ubuntu.  It worked once (idk why), and that was when I installed Linux.  I'm stuck with a Microsoft intellimouse put into a USB to PS/2 converter right now.

Where can I find drivers for it or some generic drivers that will allow me to at least use it?

---

### Post by adam.tropics on 2007-03-18
I believe the driver you would want is 'evdev' which should be installed, meaning you will want to play with your /etc/X11/xorg.conf...(back it up first though).

There is a guide [here,]("http://www.ubuntuforums.org/showthread.php?t=65471&highlight=logitech") and there are loads more on the forums, but as an example, mine (relevant bit) is below.
```

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "evdev"
    Option        "CorePointer"
    Option        "Device" "/dev/input/event9"
    Option        "ZAxisMapping" "4 5 6 7"
    Option        "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

---

