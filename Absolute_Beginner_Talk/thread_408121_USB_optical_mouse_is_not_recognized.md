---
title: "USB optical mouse is not recognized"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by iNoob on 2007-04-12
Xubuntu Edgy fails to recognize my Sony VGP-UMS1 usb optical mouse
similar problems have happened before

---

### Post by chalex on 2007-04-13
can you run "tail -f /var/log/messages" and then unplug and plug your mouse and see if a message  about a USB device shows up?

What does the "mouse" section of your /etc/X11/xorg.conf look like? mine looks like this: ```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

```

---

