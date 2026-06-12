---
title: "Resolution on Svideo out"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Katydid5283 on 2007-07-30
I would like to make my tv monitor my default display, the only problem is that the desktop is larger than the screen. (I am currently running twin view.)

I have tried every resolution available and yet I cannot get my screen to display correctly. I tried setting a virtual resolution, but the screen didn't display at all.

Below is my xorg.conf

Any thoughts?

Thank you!


Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SCN GL-1920B"
    HorizSync       30.0 - 81.0
    VertRefresh     40.0 - 76.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    BusID          "PCI:5:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"

# "800x600" "640x480"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"

# "800x600" "640x480"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"

# "800x600" "640x480"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"

# "800x600" "640x480"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"

# "800x600" "640x480"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"

# "800x600" "640x480"
        Depth       24

        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1280x1024 +0+0, TV: 1024x768 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +0+0, TV: 1024x768 +0+128"
EndSection

---

### Post by Pragmatist on 2007-07-31
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

---

