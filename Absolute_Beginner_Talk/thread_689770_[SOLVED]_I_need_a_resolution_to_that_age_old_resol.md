---
title: "[SOLVED] I need a resolution to that age old resolution problem"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by TSRep13 on 2008-02-06
So I was using Xubuntu, but I just installed Ubuntu.  I am using my Insignia NS-LCD26 TV as the monitor.  I had this same problem w/ Xubuntu, but found help and had teh reslolution fix, but now I can't seem to fix it in Ubuntu.

Here is the problem:

My TV is a 26" LCD w/ 1366x768 resolution and can handle a refresh rate of at least 85Hz.  It also seems to have an auto detect feature that is probably the biggest problem in this whole mess.  I have this connected to my good ol' Dell Dimension 8200 w/ the Pentium 4 in it.

I can't seem to get more than 800x600 61Hz out of Ubuntu though.  I have tried all the usual fixes recommended by all the forums I have read, and the Ubuntu Documentation file.  

This is what my xorg.conf says:

[PHP]Section "Device"
        Identifier      "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection
[/PHP]

I have tried adding in SubSection "Display" w/ a Depth of 24 and Modes including "1366x768@85" but it did nothing.

I have the most up to date drivers.  I'm lost.  Someone please tell me how I did it before :-)  Or at least what I can do now

---

### Post by overdrank on 2008-02-06
HI and have you tried the nvidia-glx-legacy driver that will be the nvidia driver instead of the nv.

---

### Post by ryanVickers on 2008-02-06
Did you use the restricted drivers manager? I would recommend it, if not...

---

### Post by nikoPSK on 2008-02-06
> **ryanVickers said:**
> Did you use the restricted drivers manager? I would recommend it, if not...

I would also recommend. I use it with nvidia and it's fine. :)

---

### Post by TSRep13 on 2008-02-12
Beautiful!  That did the trick. 

Thanks!

---

### Post by nikoPSK on 2008-02-12
> **TSRep13 said:**
> Beautiful!  That did the trick. 

Thanks!

no prob, glad we could help. :)

---

