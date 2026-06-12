---
title: "Screen resolution"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Dark_X on 2007-07-25
How can I get a higher screen resolution.  right now it only allows me to use 640x480.  I have a Radeon Xpress 200 series graphics card.

---

### Post by tcpip4lyfe on 2007-07-25
First make sure your ATI graphics drivers are installed.  There are lots of good how-to's on this forum on doing just that. After that, if your resolutions still isn't better:

Open your xorg.conf and check your resolutions inside:

```
gksudo gedit /etc/X11/xorg.conf
```

Look  for the following section:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
   ** DefaultDepth    24**
    Option         "XAANoOffscreenPixmaps"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
     [B]   Depth       24
        Modes      "1920x1440"[/B]
    EndSubSection
EndSection
```

First make sure your default depth is is matched in the first subsection "display" The first line in the "modes" section should be the resolution you want formatted as follows:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "XAANoOffscreenPixmaps"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1440" "1280X1024" "800x600" #etc etc etc
    EndSubSection
EndSection
```

Hope that works for you.

---

### Post by Dark_X on 2007-07-25
I already solved the problem.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

