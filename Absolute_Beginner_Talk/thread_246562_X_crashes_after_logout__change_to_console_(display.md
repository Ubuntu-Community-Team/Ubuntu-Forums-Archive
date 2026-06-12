---
title: "X crashes after logout / change to console (display black)"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by udiljak on 2006-08-29
Hi. 

As soon as I logout or try to change to the console the display turns black and I think the keyboard is also not working any more. Shutting down still works although I don't see the shutdown messages. 

I use Ubuntu 5.10. Graphik device is ATI Radeon X800 something. TFT display. 

Thanks for any advice!

Ben

From xorg.conf: 

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X800 GTO"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X800 GTO (2)"
        Driver          "fglrx"
        BusID           "PCI:1:0:1"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon X800 GTO"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```

---

### Post by udiljak on 2006-08-31
Nobody any idea? 

Please help!

---

