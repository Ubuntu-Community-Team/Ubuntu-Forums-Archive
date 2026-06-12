---
title: "Use ONLY external screen in iBook G4 ?"
date: 2007-05-15
forum: Apple PPC Users
---

### Post by bogoliubov on 2007-05-15
Hello. I have an iBook G4 12" 1.2GHz dualbooting OS X and Feisty Fawn. 
I have one xorg.conf that works with an external screen, but this is a bit slow. Also, I cannot use Desktop Effects with this setup.

Can I change Xorg.conf so that ONLY the external screen is used? If so, how and can I use Desktop Effects with this setup?

I'd really appreciate any help on this!

---

### Post by stmiller on 2007-05-15
There are some tips in the PPCFAQs at the link below for getting DVI out working, as well as 3D effects. 3D effects are buggy at best with PPC Linux, because of the lack of good 3D drivers.

Running an external monitor is putting more on the graphics card, as well as turning on Beryl. So it may be too much to do both, but you can try.

---

### Post by bogoliubov on 2007-05-16
Well I have optimized xorg.conf a bit, so the 3d performance is OK, although it's much better in OS X of course.

My problem is how to set up xorg.conf so that I only use the external monitor. If I succeed with this, Desktop effects will be the next issue, but that is not extremely important..

---

### Post by bogoliubov on 2007-05-16
I've solved it! However, it's not as fast as I had hoped for, nor does Desktop effects work OK.
Anyhow, these are the settings that I've used: (note that these settings are for a specific monitor!)




Section "Device"
        Identifier      "ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "DRI" "true"
        Option          "ColorTiling" "on"
### XAA is faster than EXA, at least on Xorg Jan 2007
        Option          "AccelMethod" "XAA"
        Option          "XAANoOffscreenPixmaps"
        Option      "AGPMode" "4"
        Option      "AGPFastWrite" "on"
####    Option      "EnablePageFlip" "on"
        Option          "UseInternalAGPGART" "no"
        Option      "ColorTiling"   "on"
### RenderAccel should be enable by default if its supported
#       Option      "RenderAccel" "true"
        Option      "UseFWPLL" "true"
        Option      "EnableDepthMoves" "true"
        Option      "backingStore" "true"
        Option          "AllowGLXWithComposite" "true"
### External screen only...
        Option          "MonitorLayout" "NONE, CRT"
        Option          "DynamicClocks" "on"
        Option          "MergedFB" "true"
EndSection

Section "Monitor"
        Identifier  "COLOR LCD"
        Option      "LVDS"
EndSection

Section "Monitor"
        Identifier      "EXTERNAL"
        Option          "VGA"
        HorizSync       30-82
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
    Monitor     "EXTERNAL"
            DefaultDepth    24
        SubSection "Display"
                Depth       24
                Modes "1280x1024" "1024x768" "800x600"
EndSubSection

---

