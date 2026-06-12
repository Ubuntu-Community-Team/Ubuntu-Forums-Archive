---
title: "Scolling question"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-10-10
I know in windows when you pushed down on the mouse wheel it would make yoer scrolling faster and easier. It doesn't seem to happen in ubuntu. Is there any program/ something I can do to enable this feature? Because It helps me alot.

Thanks,
Niko:KS

---

### Post by milosz.galazka on 2007-10-10
Look at this fragment from /etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
_**        Option          "ZAxisMapping"          "4 5"**_
        Option          "Emulate3Buttons"       "true"
EndSection

---

### Post by nikoPSK on 2007-10-10
> **milosz.galazka said:**
> Look at this fragment from /etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
_**        Option          "ZAxisMapping"          "4 5"**_
        Option          "Emulate3Buttons"       "true"
EndSection

Okay, what do I do with that?:confused:

---

### Post by milosz.galazka on 2007-10-10
To enable mouse wheel scrolling you need a line  ***Option "ZAxisMapping" "4 5"*** in your mouse section in xorg.conf configuration file. But you are searching for a way to speed it up...
My mistake :)

---

### Post by nikoPSK on 2007-10-10
say wha?

Anyways is there some way to configure this in a terminal:)

---

### Post by nikoPSK on 2007-10-14
so what i mean is:

Scrolling with mouse wheel = fast
Clicking down on mouse wheel then moving mouse up or down or left or right = Faster

How do I enable that?

---

