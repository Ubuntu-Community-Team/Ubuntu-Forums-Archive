---
title: "Screen resolutions in xorg.conf not listed in preferences"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by gnoel on 2007-06-09
I just upgraded from Edgy to Feisty, and everything looks fine so far except I can't select my screen resolution.  I am only presented with 800x600 resolution and 50 hz refresh rate on the Screen Resolution tab.  I am running an older version of the nvidia driver (1.0-7184) that I manually installed.  The driver is working fine - I can run Google Earth with no problem.  I backed up xorg.conf and ran dpkg-reconfigure, then reapplied my changes so that xorg.conf now contains the following, (the same as they were under Edgy):

> Section "Device"
        Identifier      "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-86
        VertRefresh     50-180
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1024x768" "800x600" "640x4
80"
        EndSubSection

*[etc. etc. up to a Depth of 24]*



Upon restarting x, I am still only presented with 800x600 resolution and 50 hz refresh rate.

I read in another thread that xserver might be overriding the config settings by trying to autodetect the monitor, and I can say that there is nothing unusual about my monitor (ViewSonic E90) or the connection to the video card.  The monitor is turned on during the entire boot process.

I'd be very glad if someone could help me get my full panoply of screen resolutions back.  Thanks!

---

### Post by Ek0nomik on 2007-06-10
Since the reconfigure command didn't work I tried to find a few things that other people have reported.

In your xorg file, is there a line that reads:  "UseEdid"?

Also, this thread may be of some assistance:  [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by gnoel on 2007-06-10
Thanks for your reply.  I have no line referring to Edid in xorg.conf, but I did find something potentially interesting in the xorg log file:

> Virtual screen size determined to be 800 x 600

The entire context is:

> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce3 Ti 200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 03.20.00.28.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce3 Ti 200 at PCI:1:0:0:
(--) NVIDIA(0):     @@@ (CRT-0)
(--) NVIDIA(0): @@@ (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "640x480"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default


I'm wondering if I should just upgrade to the latest version of the nvidia driver - though I thought I had read that this was the correct version for older cards (geforce3).

---

### Post by Wim Sturkenboom on 2007-06-10
Add *Option "UseEdid" "FALSE"* to the device section. It should prevent the system from using the EDID info from the monitor.

The other option that you can try is *Option "UseEdidFreqs" "FALSE"* although that would be more applicable if the resolution is there but the max refresh rate can not be used..

Hope it helps.

---

### Post by gnoel on 2007-06-10
You so rock!  This worked just fine - something to add to my knowledge store.

Thanks Ek0nomik and Wim!

---

