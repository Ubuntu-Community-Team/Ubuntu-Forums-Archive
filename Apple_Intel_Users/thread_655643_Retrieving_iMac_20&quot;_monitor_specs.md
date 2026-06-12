---
title: "Retrieving iMac 20&quot; monitor specs?"
date: 2008-01-01
forum: Apple Intel Users
---

### Post by dgm on 2008-01-01
Hey there.

Apparently the new ATI Catalyst 7.12 driver requires manually entering monitor specs in xorg.conf to get widescreen resolutions working, which is a slight issue with my 20" first-gen Intel iMac (1680x1050).

I can get a modeline by reverting back to Catalyst 7.11 and using "xvidtune -show", but does anyone know how to find Horizontal Sync and Vertical Refresh rates? Catalyst 7.12 will not work without them. Apple doesn't seem to have released these specs, but is there a way to revert to 7.11, and find out what specs are being used?

If not, forgive my ignorance on video card drivers, but any other help would be greatly appreciated.

~dgm

---

### Post by cyberdork33 on 2008-01-02
They are the same for the 20" cinema display (since they are actually the same panel...)

```

Section "Monitor"
    Identifier      "Apple Cinema Display"
    VendorName      "Apple Inc."
    ModelName       "Apple Cinema Display 20"
    HorizSync       28-90
    VertRefresh     43-72
    DisplaySize     434 270
    Option "DPMS"
    UseModes "Modes0"
EndSection

Section "Modes"
    Identifier "Modes0"
    ModeLine "1680x1050" 119.00 1680 1728 1760 1840 1050 1053 1059 1080
    Modeline "1280x800" 67.26 1280 1312 1560 1592 800 817 824 841
    Modeline "1024x640" 51.90 1024 1056 1248 1280 640 653 660 673
    Modeline "800x500" 30.98 800 832 944 976 500 510 515 526
EndSection
```

---

### Post by ward83 on 2008-01-04
This is all I have in mine, and it's working fine (20" core2 iMac, running gutsy):
```

Section "Monitor"
        Identifier      "Color LCD"
        Horizsync       30.0    -       100.0
        Vertrefresh     50.0    -       160.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Option          "UseFBDev"      "true"
        Busid           "PCI:1:0:0"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Color LCD"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1680x1050"
        EndSubSection
EndSection


```

---

### Post by cyberdork33 on 2008-01-04
BTW, from the notes:
[FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2][quote=https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_712_linux.html#183417]Custom mode lines in xorg.conf may be ignored by the fglrx driver[/quote][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

