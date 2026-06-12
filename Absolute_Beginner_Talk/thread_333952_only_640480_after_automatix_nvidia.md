---
title: "only 640*480 after automatix nvidia"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by waxfactor2nd on 2007-01-08
hi ive just installed the nvidia driver via automatix but now i only can choose 640*480 in the screen resolution menu. this is a 1280*1024 screen so it is very anoying. how can i make it back to 1280*1024. it is a 6600gt and im running edgy.

---

### Post by taurus on 2007-01-08
Go back into Automatix and remove the nVidia driver!  Then, use this guide if you wish.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by waxfactor2nd on 2007-01-08
arent there any easyer way??

---

### Post by waxfactor2nd on 2007-01-08
that is completed but i still cant set the resolution higher, so what shall i do

---

### Post by _simon_ on 2007-01-08
from terminal:

```

sudo gedit /etc/X11/xorg.conf

```

Loacate your Section "Screen" and within that, Subsection "Display" and check that higher resolutions are listed - only list resolutions that you know your monitor can support though.

This is mine as an example:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"
    Option         "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

If you add any in then you need to restart X so once you have saved your changes do CTRL ALT BACKSPACE and log back in.

---

### Post by xopher on 2007-01-08
In newer drivers nvidia-settings also offer a way of changing the resolution. If all else fails, which it shouldn't, you could try that. Remember, only works with newer drivers, not the ones in the official repository. If I recall correctly that is.

---

### Post by woul on 2008-01-25
i had the same problem, but using restricted drivers package. solved by editing xorg.conf, as cited above.  tks =D

---

