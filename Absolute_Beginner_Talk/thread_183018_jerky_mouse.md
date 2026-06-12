---
title: "jerky mouse"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by skippy81 on 2006-05-27
Hi I am using a Razer Diamondback optical mouse.  Ive noticed that it seems impossible to move the mouse just 1 pixel at a time, it seems to jerk as if its snapping to an invisible grid every 5 pixels or so. 

Can anyone suggest how I can improve the resolution of my mouse.  The mouse settings in the gnome gui dont change anything.

---

### Post by zhoux on 2006-05-27
you can edit the xorg.conf file:
```

sudo gedit /etc/X11/xorg.conf
```

Scroll down to:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Buttons"        "7"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection
```

Then at the end add the line:
    ```
Option        "Resolution"   "100"
```

You can change the 100 to anything you want.

Save the file and restart gdm.

```
Ctrl+Alt+Backspace
```

---

### Post by skippy81 on 2006-05-27
Thankyou, its done the trick :P

---

