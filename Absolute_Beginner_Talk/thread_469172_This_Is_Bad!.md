---
title: "This Is Bad!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-09
```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Im using Nvidia 5200 Geforce Generic...
Is it bad that it says Generic?

Im trying to install Compiz...

---

### Post by overdrank on 2007-06-09
> **LollYouSuckZor said:**
> ```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Im using Nvidia 5200 Geforce Generic...
Is it bad that it says Generic?

Im trying to install Compiz...

Hi its not bad it still using the nvidia chipset! ;)

---

### Post by NeoLithium on 2007-06-09
There's a section on NVIDIA drivers at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) if you want to install those.  Though if it's working, it's not bad at all :)

---

### Post by LollYouSuckZor on 2007-06-09
Phew :D Thanks

---

