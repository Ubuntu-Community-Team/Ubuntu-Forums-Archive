---
title: "Display Monitor Resolution &amp; Refresh Rate Problem -- xorg.conf"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by anguste on 2006-10-31
My display monitor should support 1024x768 @ 100Hz (as it does in Win). But by default in my ubuntu 6.06 the refresh rate is 85Hz in 1024x768, and there is no further options for frequency in this resolution. 

I can also set the resolution to 1280x1024 at 85Hz using "System - Preferences - Screen Resolution", but I simply can not set a 100Hz frequency at 1024x768... 

So I tried to modify the /etc/X11/xorg.conf file, as is listed below:

```

Section "Monitor"
    Identifier     "DPro740SB"
    Option         "DPMS"
    HorizSync      31-96       # I added this line according to the info provided with the monitor's manual
    VertRefresh    55-160      # same as above
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
    Driver         "nvidia"
    Option         "NoLogo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
    Monitor        "DPro740SB"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
    EndSubSection
    SubSection     "Display"
        Depth       4
    EndSubSection
    SubSection     "Display"
        Depth       8
    EndSubSection
    SubSection     "Display"
        Depth       15
    EndSubSection
    SubSection     "Display"
        Depth       16
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_85" "1024x768_100"  # I added the "_85" and "_100" part, hoping to set a fixed refresh rate..
    EndSubSection
EndSection

```


After the changes I restarted the computer, and I get now a 1280x1024 @ 85Hz screen resolution, which I don't want actually (things are too small to see clearly..). 

But now when I go to "System - Preferences - Screen Resolution", there is no other options for me to choose, not even the 1024x768 line. That's so wierd, can anybody please tell me why? And how to fix this if possible. Thanks a lot.

---

### Post by daou on 2006-10-31
Check this link, especially the section that shows how to make a modeline

[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

