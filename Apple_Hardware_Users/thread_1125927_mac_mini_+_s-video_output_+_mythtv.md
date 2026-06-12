---
title: "mac mini + s-video output + mythtv"
date: 2009-04-14
forum: Apple Hardware Users
---

### Post by poerschr on 2009-04-14
I am having problems with s-video output on a mac mini (running mythbuntu).  The system fails to load mythtv upon startup.  My mouse cursor is visible, but when I click on the applications button (on the top left), the submenu does not appear.  Clicks have no response.  When connected to the monitor, everythign works great.  

I have read this guide here:

[http://www.mythtv.org/wiki/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu](http://www.mythtv.org/wiki/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu)

An attempted to use the following code (makeing changes to the intel driver, becasue I understand that it is old
```

Section "Device"
        Identifier      "Intel"
        Driver          "Intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
        Option      "TVStandard" "NTSC"
        Option      "TVOutFormat" "COMPOSITE"
        Option      "TVOverScan" "0.6"
        Option      "ConnectedMonitor" "TV" # Add this if you're having problems
        Option "XAANoOffscreenPixmaps" "true"
EndSection


```

The changes that I made appear to have no effect.  I read on another guide that xorg.conf is not used anymore (or something to that effect).  My orginal xorg.conf file had almost no information on it.

Thank you..

---

