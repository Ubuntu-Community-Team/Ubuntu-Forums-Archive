---
title: "Problems with Geforce 440 MX"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Oobowo on 2007-05-10
Hi, I'm new to Linux and Ubuntu, so please have patience with me.

I have recently installed Feisty Fawn. My pc specs:

Pentium 4 1.5Ghz
Geforce 440 MX videocard
384MB RAM
Proline CrystalView 7Glr monitor
Samsung CDMA modem (through phone)

The install works perfectly fine, although my refresh rates and resolutions are messed up slightly. Automatically starts in 1280 x 768 resolution @ 60 hz refresh, I don't get any other options for refresh rate either, set this to 800 x 600 and still only 60hz refresh (doesn't want to do 1024 x 768 for some strange reason. Anyway, I figure the problems will be sorted out once I install the NVidia drivers, right? So I install the nvidia-glx driver (not legacy, cause that's for older chipsets as I read on forums), but then X doesn't want to load. So, I reload xorg.conf and restart X. Cool, now (probably should have a different thread for this) my modem isn't detected. Checked the logs and saw that it isn't being assigned to /dev/ACM0 as normal. So I restart the entire system. Ok, modem works again, but now I still have driver problem.

Can anyone pleeeeeze help? I've tried Envy(didn't work), I've tried a lot of different drivers (legacy,glx). What's up with this? And can you please explain to me why the modem isn't loaded either?

Thank you very much.

Oobowo.

---

### Post by Tucatts on 2007-05-10
I have the same card and I went to System-Administration-Restricted Drivers manager. I checked enable and that was that, it loaded the drivers and the card works fine. Try that.

---

### Post by Oobowo on 2007-05-11
Ok, cool. Thanks Tucatts. Driver seems to be working fine. But now, I still have a problem with the resolution and refresh rate. I only have one option. 800x600 @50Hz . I've tried dpkg-reconfigure, but there's still no difference (restarted multiple times) Here's what a part of my xorg.conf looks like at the moment:

Section "Device"
        Identifier      "Nvidia Geforce 440 mx"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Nvidia Geforce 440 mx"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Thanks!
Oobowo

---

