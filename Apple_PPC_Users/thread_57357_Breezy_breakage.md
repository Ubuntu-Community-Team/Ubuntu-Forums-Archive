---
title: "Breezy breakage"
date: 2005-08-16
forum: Apple PPC Users
---

### Post by calum on 2005-08-16
Recent updates to Breezy (since about last Friday) have caused the scrollwheel on my Wacom Graphire to stop working... anyone else seeing this, or know how to fix it off-hand?

---

### Post by GavinX on 2005-08-16
I had a similar problem; it seems that the update removed the ZAxismapping from Xorg. Follow these steps and you should be able to solve it:
1. sudo gedit /etc/X11/xorg.conf
2. look for this section and insert the part highlighted in red then reboot:

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    [color=Red]Option         "ZAxisMapping" "4 5"

[color=Black]Cheers,
GavinX
[/color][/color]

---

### Post by calum on 2005-08-17
[QUOTE=GavinX]I had a similar problem; it seems that the update removed the ZAxismapping from Xorg. [/QUOTE]

Cool, that was it... knew it was probably something simple :)

---

### Post by GavinX on 2005-08-17
Great. Enjoy the Ununtu special blend!

---

