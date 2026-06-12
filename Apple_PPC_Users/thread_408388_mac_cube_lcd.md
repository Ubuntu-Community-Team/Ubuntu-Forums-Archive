---
title: "mac cube lcd"
date: 2007-04-13
forum: Apple PPC Users
---

### Post by Dan194 on 2007-04-13
I am new to linux and have just received a Mac cube  with a rage 128 video card and a 15 inch cinema lcd display.I have tried a number of versions of linux on it and they all display fine on a crt monitor and work fine on boot up.When I install linux with the lcd hooked up it will install fine but on boot the screen will stay blank.It has done this with every version of linux I have tried so I am guessing that something is set wrong in the software.I have searched for months on the web and have yet to find the answer.If someone knows could they please help this newbe to linux.Thanks in advance

---

### Post by avtolle on 2007-04-13
I have a Cube with the Studio LCD display; below is the part of my xorg.conf file as to video settings. If these are different from yours, I would suggest editing said file and using the values I have, which have "always just worked" for me in 6.06.1 LTS.

Section "Device"
    Identifier    "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
    Driver        "ati"
    BusID        "PCI:0:16:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Apple Studio"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
    Monitor        "Apple Studio"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

---

