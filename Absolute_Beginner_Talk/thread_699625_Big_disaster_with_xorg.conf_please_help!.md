---
title: "Big disaster with xorg.conf please help!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2008-02-17
hi!

I edited the xorg.conf file as says [https://help.ubuntu.com/community/MacBook#touchpadtweaks](https://help.ubuntu.com/community/MacBook#touchpadtweaks) in order to alter the section:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
'''...insert other options from below here...'''
EndSection

Now after pressing control+alt+backspace and login the deskop doesn't load.

Anyone can paste here that standard Synaptics Touchpad section in order to edit the file again (unfortunately I didn't make a backup) and enter to the desktop again?

Thanks I really need help here!!

---

### Post by (((X))) on 2008-02-17
...

---

### Post by fredscripts on 2008-02-17
Thank you very much!!

---

