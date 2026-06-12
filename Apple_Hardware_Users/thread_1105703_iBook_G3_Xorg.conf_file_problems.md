---
title: "iBook G3 Xorg.conf file problems"
date: 2009-03-25
forum: Apple Hardware Users
---

### Post by hamstersquasher on 2009-03-25
Hello all, 

I have a 12" iBook G3 500MHz running Ubuntu 8.10.  The install went well with only a few minor hiccups but at the best I can only run my display in 'low-graphics mode'.  If I run ```
sudo lspci | grep VGA
```here is what i get...```
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
```Can someone please provide me with a working Xorg.conf file using the same hardware?  I am close to abandoning Ubuntu on this laptop and going for another distro :(

---

### Post by anandrajny on 2009-04-01
I've the same machine with 8.04 and adding the following in xorg.conf works for me fine. Good luck.

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "r128"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "false"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       58-62
        VertRefresh     75-117
        Option "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
        Depth 24
        Modes "1024x768"
        EndSubSection
EndSection

---

