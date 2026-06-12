---
title: "Stuff in the xorg.conf"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by chopsuey on 2007-02-16
nr1:
Could someone please tell me what this is(its in the xorg.conf file), and what it does:

Load        "dri"

Option	   "RenderAccel" "true"
Option	   "AllowGLXWithComposite" "true"

Option     "AddARGBGLXVisuals" "True"
Option     "XAANoOffscreenPixmaps"
Option     "TripleBuffer" "True"

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Do i need it and does it give me better performance in 3d-games/programs?



nr2:
Would compiling kernel, nvidia drivers and wine from source give me better performance in 3d-games/programs?

---

### Post by jure1873 on 2007-02-17
1) it's probably there for compiz or beryl
2) yes, but I think it's not worth going trough the trouble for the small difference in performance.

---

