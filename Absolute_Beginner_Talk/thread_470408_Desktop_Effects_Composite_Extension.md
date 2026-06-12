---
title: "Desktop Effects? Composite Extension?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-10
Yeah, I just installed the Nvidia drivers, and I went to desktop effects, no dice.  I get a notice that says 

"The composite extension is not available"

What's up?

---

### Post by trent dillman on 2007-06-10
...

---

### Post by LollYouSuckZor on 2007-06-10
> **trent dillman said:**
> Have you tried restarting X? Either reboot, or CTRL+ALT+F1, log in, and ```
sudo /etc/init.d/gdm restart
```

If it still doesn't work, check your /etc/X11/xorg.conf file for the line ```
Driver "nv"
``` and change it to ```
Driver "nvidia"
```

```

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "hp f1523"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Looks fine?  Any other ideas.

OH! Im so blind.  Lol, Check that out. 

```

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Should i type in, True? or.. enable?

---

### Post by LollYouSuckZor on 2007-06-11
bumpedy...

---

### Post by steveneddy on 2007-06-11
Enable

then restart X - CTRL + ALT + BACKSPACE

---

