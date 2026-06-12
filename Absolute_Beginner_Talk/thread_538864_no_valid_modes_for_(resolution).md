---
title: "no valid modes for (resolution)"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by tedder on 2007-08-30
New install of Feisty Fawn, new machine (nVidia GeForce 6150 on the mobo).

```
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1080@60"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
```

I'm really trying to get this to display at my DFP's native resolution, 1920x1080. So I added a modeline to my monitor section:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-96
        Vertrefresh     43-60
        Modeline "1920x1080_60"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection
```

I've also added that to the screen section:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation C51PV [GeForce 6150]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1920x1080@60"  "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection
```

I have a feeling the problem is the Modes line in the Screen section. I've tried it as 1920x1080, 1920x1080_60, and 1920x1080@60. None seem to work.

What am I doing wrong?

---

### Post by phr0ze on 2007-08-30
Don't use modelines if you don't have to. First step is to make sure both refresh ranges are exactly what your monitor specifications say. Then just add the resolution to the screen area without any forced refresh.

Lets see your xorg.conf after that.

BTW: it can help if you give us the model of the DFP.

---

### Post by Hobo Joe on 2007-08-30
Do you have your drivers installed?

If so, you need to use the nVidia control panel, not the xorg or any of that.


```

sudo nvidia-settings

```
Just set it how you like and then save it to 'x configuration file'.

---

### Post by tedder on 2007-08-30
> **phr0ze said:**
> Don't use modelines if you don't have to. First step is to make sure both refresh ranges are exactly what your monitor specifications say. Then just add the resolution to the screen area without any forced refresh.

Okay, I've commented out the Modeline, changed the mode to "1920x1080", restarted X. No change. Here's the log file, with some context:
```
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.42.37
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     ONK TX-SR674 (DFP-0)
(--) NVIDIA(0): ONK TX-SR674 (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): ONK TX-SR674 (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1080"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600

```


> Lets see your xorg.conf after that.

The two relevant sections- if you want the whole thing, let me know. Only 800x600 and 640x480 are allowed on the 'screen resolution' config.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-96
        Vertrefresh     43-60
        #Modeline "1920x1080_60"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation C51PV [GeForce 6150]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1920x1080"     "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection
```


> BTW: it can help if you give us the model of the DFP.

Sure! Samsung LN-T4061F. Displays 1080p, inputs for HDMI and VGA. I'm using a DVI->HDMI cable to my receiver, HDMI->HDMI to the DFP.
[Manual for the TV](http://downloadcenter.samsung.com/content/UM/200703/20070301133755718_BN68-01178A-00L02-0216.pdf)- rates at the bottom of printed page 44, PDF page 46.

So this made me think, and I ran the DVI->HDMI directly to the TV. I got my resolution, plus everything in between. So the receiver must fool the auto-sense from the video card? How can I turn that off? Here's the module section:
```
Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection
```

I also need to fix the overscan (losing all edges).

Thanks for your help.

---

### Post by tedder on 2007-08-30
Research I've done on the overscan issue.

- Use 1840x1036. Didn't work- get "no valid modes for.."
- Add a Modeline for 1840x1036 res. Get "no valid modes for.."
- Turn off 'UseEDID'. No display. (see log below)
- 

Log after the 'UseEDID' flag is turned off:
```
(--) NVIDIA(0): DFP-0: 310.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1080"; removing.
(WW) NVIDIA(0): No valid modes for "1840x1036"; removing.
(WW) NVIDIA(0): No valid modes for "1840x1036@50"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

URLs:
[http://gentoo-wiki.com/HOWTO_Xorg_HDTV](http://gentoo-wiki.com/HOWTO_Xorg_HDTV)
[http://ubuntuforums.org/showthread.php?t=304625&page=3](http://ubuntuforums.org/showthread.php?t=304625&page=3)
[http://ubuntuforums.org/showthread.php?p=3265080](http://ubuntuforums.org/showthread.php?p=3265080)

---

