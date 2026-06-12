---
title: "[SOLVED] no vga output lenovo r61"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-10-28
so i have no out put on my vga out. i have a lenovo r61 and a presentation in about a month. any advice would be great. 

thanks

---

### Post by rickycodie on 2007-10-28
ok i found a fix.

[http://www.thinkwiki.org/wiki/Category:R61](http://www.thinkwiki.org/wiki/Category:R61)

add this to the xorg.conf in the device section

```
Section "Device"
        Identifier "Videocard0"
        Driver "intel"
        BusID "PCI:0:2:0"
        Option "MonitorLayout" "NONE,LFP+CRT"
        Option "DevicePresence" "true"
        Option "CheckLid" "false"
        VendorName "Lenovo"
        BoardName "Intel Corporation Mobile Integrated Graphics Controller"
   EndSection
```

you can also make the monitor a separate workspace if you want on that page.

---

