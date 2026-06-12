---
title: "Panels with dual monitors"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-05-25
Ok, I have dual monitors setup with Twinview, and the way it's setup is there is a top and bottom panel on one screen, and the bottom panel just shows the windows for both screens, but I was wondering if there was a way to make it so that I can have a bottom panel on both screens, and have them show up the windows in their respective screens. (e.g. if I have FF open in screen one, it will show up in the the panel on that screen, and if I have Pidgin open on screen 2, it will show up on screen 2's panel.)

That would be awesome. :)

---

### Post by Soybean on 2007-05-25
Hmm. Not that I know of. Twinview "more or less" makes your two monitors act like one really big monitor. 

Although, if you don't need to be able to drag windows from one monitor to the other, I believe it's possible to set up two X servers, one for each monitor. That's not TwinView anymore, and I've never actually done it (I like dragging my windows all over the place ;)), so I don't know exactly how, but I hear it can be done. Under that sort of a setup, I'm sure the panels would work like you're describing.

---

### Post by bodhi.zazen on 2007-05-25
Nice cat.

Yes it can be done. Best WM for twinview is xfce ...

Otherwise you need to hand configure your monitors. Like this : [http://ubuntuforums.org/showthread.php?&t=240150](http://ubuntuforums.org/showthread.php?&t=240150)

Yea the how to is written with *box in mind, but it will give you what you want with gnome/xfce/kde if you like.

You can try:

```
gksudo nvidia-setings
```

Try to configure independent monitors (NOT TWINVIEW) and save xorg.conf

In my experience this does not work well.

---

### Post by Nythain on 2007-05-25
only way you are gonna be able to do it is like already said, set up two desktops... i achieved it like this with my xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "STAC Electronics KDS VS-70"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          0
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
    Option         "NoPowerConnectorCheck"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          1
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
    Option         "NoPowerConnectorCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
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

```
notice how i set up two screens, display devices and monitors and made sure Xinerama was off ("0")

once again, only problem is you cant drag apps between the two, wich was no problem for me, and you will have to set up each desktop, though they will share panel and other kde settings

---

### Post by Hobo Joe on 2007-05-25
Well, considering that I can't do it without separating my desktops, I don't think I'll do it, it's not a big deal, just something that would be kind of nifty.

Thanks anyway though.

---

