---
title: "How do I set  xgamma -gamma to 1.2 on startup?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-04-19
My Screen is getting old. And is a little to dark in the brightness. 

Anyhow, it looks good as new when I set  xgamma -gamma to 1.2
```
 xgamma -gamma 1.2
```

But know I have to do this everytime I turn on my PC. How can I set default to 1.2? Or atleast let it set  xgamma -gamma to 1.2 everytime I startup my PC?

Thanks

---

### Post by yabbadabbadont on 2007-04-19
You can add a "Gamma" option to the "Monitor" section of your /etc/X11/xorg.conf file to automatically set the gamma everytime X windows is started.  You will need to use sudo when you edit that file.  As an example, here is my Monitor section in which I set the gamma to 0.75 for the Red, Green, and Blue channels.
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-80
        DisplaySize     306 230
        Gamma           0.75 0.75 0.75
EndSection

```
Even though I have the value in there for each of the three color channels, you can just use one value instead.  (If only one value is provided, it is used for all three color channels.)

---

### Post by aktiwers on 2007-04-19
Thanks!

Mine only had this though:
> Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        
EndSection

But I just added the Gamma 1.2 and it seams to work after restarting my x-server.

Thanks a lot! :)

---

