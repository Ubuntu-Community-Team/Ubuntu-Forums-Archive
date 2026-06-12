---
title: "X problems with 6.10 G4 PowerBook (5.9)"
date: 2006-11-09
forum: Apple PPC Users
---

### Post by l390 on 2006-11-09
Hi !

I got problem with X after upgrading my G4 1,67 Ghz G4 to 6.10. The problem is that I do not get a X login screen during boot sometimes. I just see the cursor at the top left corner and nothing happen. The system also does not respond to key strokes. So I have to switch the system off. Sometimes the next boot succeeds but sometimes I need several tries.
I'm using: Xorg 7.1.1 with a Radeon 9600/9700 M10/M11.
Here a part of my xorg.conf
```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050"
```

All ideas are appricated.

Regards Steffen

---

