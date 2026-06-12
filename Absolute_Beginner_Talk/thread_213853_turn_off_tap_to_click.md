---
title: "turn off tap to click"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-07-11
i can't figure out how to turn off "tap to click" on my touch pad.  here are the contents of my xorg file:


```
Section "InputDevice"
     Identifier     "Configured Mouse"
     Driver         "mouse"
     Option         "CorePointer"
     Option         "Device"             "/dev/input/mice"
     Option         "Protocol"           "ExplorerPS/2"
     Option         "ZAxisMapping"       "4 5"
     Option         "Emulate3Buttons"    "true"

EndSection
```

Thanks,
-steve

---

### Post by Paerez on 2006-07-11
that is the mouse section, your issue is probably in the touchpade section, which is usually named "Synaptics something" or "ALPS something"

post that plz.

---

### Post by stevieb on 2006-07-11
> **Paerez said:**
> that is the mouse section, your issue is probably in the touchpade section, which is usually named "Synaptics something" or "ALPS something"

post that plz.

nothing like that in the file; sorry. no synaptics or alps.

-steve

---

### Post by skrållarn on 2006-07-14
take a look at [bug 47971]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/47971")

---

