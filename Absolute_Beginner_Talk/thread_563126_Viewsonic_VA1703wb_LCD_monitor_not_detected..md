---
title: "Viewsonic VA1703wb LCD monitor not detected."
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by cthullu2 on 2007-09-29
HI.  I recently got a Dell Inspiron 531s Desktop with a Viewsonic VA1703wb LCD monitor and an NVIDIA GEFORCE 6150 LE INT Graphics GPU.  Ubuntu recognized it as a VESA CRT monitor.  I enabled the NVIDIA drivers and rebooted and edited the xorg.conf file so the resolution would be 1400 x 900 and rebooted again.  No luck.  1224 x 768 is the max resolution I can enable.  If I go to sudo nvidia-settings, I cannot change the CRT to LCD.  It has a "configure" button to be able to change it but when I click on it, nothing happens.  It says "open new x window?" and I click on "yes" and nothing happens.  No error message.  I tried formatting and reinstalling ubuntu and I tried the "ENVY" program to try to get NVIDIA Graphics working right, but it still won't recognize that I have an LCD and not a CRT monitor.

Please help on how I can get my monitor to be recognized as an LCD monitor and to get it to stay at 1400 x 900 resolution.  Thanks.  Here is my xorg.conf file:


Section "Device"
        Identifier      "NVIDIA GeForce 6150"
        Driver          "vesa"
        BusID           "PCI:0:13:0"
EndSection

Section "Monitor"
        Identifier      "ViewSonic VA1703wb"
        Option          "DPMS"
        HorizSync       24-82
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce 6150"
        Monitor         "ViewSonic VA1703wb"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection


 SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by dcstar on 2007-09-29
> **cthullu2 said:**
> HI.  I recently got a Dell Inspiron 531s Desktop with a Viewsonic VA1703wb LCD monitor and an NVIDIA GEFORCE 6150 LE INT Graphics GPU.  Ubuntu recognized it as a VESA CRT monitor.
.........

Try installing the **discover1** and **xresprobe **packages, then (in a terminal) do:

```
sudo dpkg-reconfigure xserver-xorg
```
and see if things behave differently.

---

### Post by cthullu2 on 2007-10-01
Thanks for your fast reply.  I installed the discover1 and xresprobe packages, rebooted, ran sudo dpkg-reconfigure xserver-xorg and it could not detect my monitor.  It never gave me the option of selecting an LCD instead of a CRT monitor.  I put in the correct horizontal and vertical refresh rates, but after rebooting, it said there was a problem with the monitor.

---

