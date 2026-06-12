---
title: "xorg.conf intel 845"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2008-02-24
Someone told me to change the device section to this
```

Identifier "Intel Corporation 82845/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Bus ID "PCI:0:2:0"
Driver "i810"
Option "XAA NoOffScreenPixmaps"
Option "RenderAccel" "True"
Option "AllowGlXWithComposite" "True"
Option "Add ARGBXVisuals" "True"
VideoRam 65536

```

I had written this on a piece of paper back then. Should I change anything in it or will it work fine. Also, Are there any spelling mistakes or places where I might have messed with the space between charachters ?

---

### Post by (((X))) on 2008-02-24
Why do you want to edit that script anyway?just curious:)

Try to boot using it, if something may go wrong..
Boot in safe mode and edit xorg script with nano, simple command-line editor comes standard with ubuntu.

---

