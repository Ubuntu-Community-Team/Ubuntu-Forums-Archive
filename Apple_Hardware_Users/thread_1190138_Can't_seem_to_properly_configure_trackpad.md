---
title: "Can't seem to properly configure trackpad"
date: 2009-06-17
forum: Apple Hardware Users
---

### Post by Malart on 2009-06-17
Hi, I have a Poverbook G4 aluminum 15" with a 128 MB ati mobility that i have just now been able to get working well... but my trackpad will absolutely not let me look while typing, so no fps fun for me. I have tried many tutorials that all seem to revolve around enable SHMConfig in xorg.conf, and i have the option in there, but gsynaptics doesnt seem to recognize it, and i can't find the option in the menus to disable the trackpad while typing so i can get rid of it.


i have tried mouseemu as well, and have had no luck


```

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
    Option        "SHMConfig"        "on"
EndSection
```

Im about to head out, most likely wont have internet untill tommorow, but ill try to look in on the thread if i get a chance.

---

### Post by tiagobt on 2009-06-17
What Ubuntu version do you have? Have you tried to configure the trackpad using an FDI file (inside /etc/hal/fdi/policy) instead of xorg.conf?

---

### Post by Malart on 2009-06-18
Thanks for responding Tiagobt. I actually figured it out on my own. I had already installed mouseemu, and saw in the man that it used something called uinput, which i don't have. So what i did was make a symlink to my adb trackpad and named it uinput, and now mouseemu recognizes my mouse. I can now use the mouse while holding a key down, and i can scroll holding alt down, plus emulate all 3 mouse buttons.

---

