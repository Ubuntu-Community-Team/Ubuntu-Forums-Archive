---
title: "[SOLVED] iMac fglrx default resolution"
date: 2007-11-29
forum: Apple Intel Users
---

### Post by AlainJLEB on 2007-11-29
Hi there,

I have successfully installed ATI driver, and I can get upto 1920*1200 ... but I have to change the resolution settings each time I boot up the iMac.

When I log in, the resolution is set to 1600*1200, and I have to launch the ATI Catalyst Control Centre to put it at 1920*1200. Is there a way of having it by default at 1920*1200? xorg.conf mentions this mode as the unique one:
```
Section "Monitor"
        Identifier   "Color LCD"
        HorizSync    28.0 - 96.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc ATI Default Card"
        Monitor    "Color LCD"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1920x1200"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

Help appreciated :)

---

### Post by cyberdork33 on 2007-11-29
add the mode line to the ati-config screen section:
```

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1920x1200"
        EndSubSection
EndSection
```

The other screen section and the vesa device section are not needed.

---

