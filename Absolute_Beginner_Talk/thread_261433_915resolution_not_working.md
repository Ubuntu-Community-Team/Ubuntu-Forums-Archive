---
title: "915resolution not working"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by popcorn09 on 2006-09-20
Hi,

I want to change my desktop resolution. I tried to install 915resolution for it but it gave the following error:

> Unpacking 915resolution (from .../915resolution_0.5-1ubuntu6_i386.deb) ...
Setting up 915resolution (0.5-1ubuntu6) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.

Any idea what is wrong?

Thanks.

---

### Post by bitoiu on 2006-09-20
Hi,

I'm not sure You can do this safely. I had the same trouble with a diferent card and couldn't use 915 resolution. So i went to /etc/X11/xorg.conf and added a display mode:

> Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

The "1280x800" Resolution was added manually by me, so maybe you can try and do this yourself, but its best to wait for someone with more knoledge to say this is safe ;)

---

### Post by popcorn09 on 2006-09-20
Well I've done this with SuSE Linux once... don't know what the safety issues could be.

---

