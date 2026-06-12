---
title: "Any way to get my third mouse button to scroll sideways too?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2006-12-07
My current xorg.conf file allows my third mouse button on my thinkpad to scroll vertically.  I seem to recall there being an option I can throw in that would let it scroll side to side too.  Anyone have any ideas?  Here is my current xorg.conf:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
        Option      "EmulateWheel" "true"
        Option      "EmulateWheelButton" "2"
EndSection
```

---

### Post by lognok on 2007-01-17
Sorry, can't help you on that one, but thanks for enabling vertical scroll for me :D , I have been missing that feature for a long time...

---

### Post by jsully1 on 2007-01-18
Haha, happy to help!

---

