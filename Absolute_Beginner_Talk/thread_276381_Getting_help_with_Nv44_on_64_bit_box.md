---
title: "Getting help with Nv44 on 64 bit box"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Bobajot on 2006-10-12
I'm currently running Ubuntu (loaded Sunday) and I'm baffled on how to set up the Nvidia drivers for a AM2NF4G-SATA2 (Asrock) 64 bit X2 for its standard graphics NV44 DX9.0 VGA. I'm running the 64 bit version of Ubuntu. Any help or links for same would be greatly appreciated. I also have a Samsung 913N (SyncMaster) which can calibrate higher than the standard settings bt don't know how to do this easily.:-?

---

### Post by Bobajot on 2006-10-12
Well I loaded something called Automatix2 then loaded the nvidia driver with that and rebooted. That solved the first issue and the second is probably just editing **/etc/X11/xorg.conf** so I'll give that a go tomorrow. Hope this helps somebody else.:) 
**/etc/X11/xorg.conf** relevant bit
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection

---

### Post by Bobajot on 2006-10-13
I edited the xorg.conf file but the machine refused to load Xwindows. I put the original /etc/X11/xorg.conf back and it now works. There is obviously more required to get higher resolutions but I'm stuck for now.
 
This was the **xorg.conf** that failed
Section "Monitor"
    Identifier     "SyncMaster 913N Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    DisplaySize     377-302
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster 913N Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Bobajot on 2006-10-13
Good to go:) :) 

Changed default depth to 16 in xorg.conf and removed DisplaySize 377-302

It was probably the Depth that was causing the problem.

Nice to have had so much help but running Windows I'm used to getting None:p

---

