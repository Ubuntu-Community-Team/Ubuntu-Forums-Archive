---
title: "Xorg.conf + emac = 110% frusteration."
date: 2009-03-01
forum: Apple Hardware Users
---

### Post by jeffadams78 on 2009-03-01
OK.  I've installed 8.10 on my emac (1.25ghz "USB 2.0" emac).

I did the modprobe idescsi thing, got the sound working, set up the dual boot with OSX, etc.

But I can NOT get the @#%$(*#(%@# xorg.conf set correctly to save my life.

I've tried like 3 or 4 different xorg.conf's posted by various people who claim to have emacs.  I've set the refresh rate, used read-edid to get the modelines, etc.

And yet, I have exactly two options.

Xorg.conf with ANYTHING in it (at least, anything I've tried): Blank scren.

No xorg.conf (delete the file): Low graphics mode.

If I could even figure out what to put in xorg.conf to get the exact same behavior as low graphics mode I would be thrilled, because at least I'd have a starting point!

Can we start there?  Does anyone know what a "low graphics mode" xorg.conf would look like?

---

### Post by jeffadams78 on 2009-03-01
Oh and one more thing: Can someone please tell me a simple way to restart X without having to reboot?  I.E. I edit xorg.conf, get a blank screen, I can switch to a terminal, make another xorg.conf edit, then....   sudo kill something?  startx?

---

### Post by jeffadams78 on 2009-03-01
Isn't it amazing how you can't figure something out until you ask?

I was missing the 'Driver      "fbdev"' line.

For those other emac users out there, the following is my (now working) xorg.conf:

(and yes, it's an eMac, the monitor is called "iMac" because that's how read-edid identifies it).

```
Section "Device"
        Identifier      "Radeon9200"
        BusID           "PCI:0:16:0"
        Driver          "fbdev"
        Option          "UseFBDev"              "true"
EndSection

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "iMac"
        VendorName "APP"
        ModelName "iMac"
        # Block type: 2:0 3:fd
        HorizSync 71-73
        VertRefresh 70-140
        # Max dot clock (video bandwidth) 130 MHz
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no
        Option  "DPMS"

        Mode    "1024x768"      # vfreq 88.995Hz, hfreq 72.086kHz
                DotClock        99.190000
                HTimings        1024 1072 1168 1376
                VTimings        768 769 772 810
                Flags   "+HSync" "+VSync"
        EndMode
        Mode    "1280x960"      # vfreq 71.932Hz, hfreq 72.075kHz
                DotClock        122.240000
                HTimings        1280 1328 1424 1696
                VTimings        960 961 964 1002
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Radeon9200"
        Monitor "iMac"
        DefaultDepth 24
        SubSection "Display"
                Depth 8
                Modes "1280x960" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth 15
                Modes "1280x960" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1280x960" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1280x960" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
        Screen "Default Screen"
EndSection
```

---

