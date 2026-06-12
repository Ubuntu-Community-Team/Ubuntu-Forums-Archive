---
title: "login screen resolution"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by brotherlu on 2007-06-14
Hi guys, i have a problem in the beginning ubuntu did not recognize my monitor so i had to fix my xorg.conf as such

```
Section "Monitor"
        Identifier      "IBM E74"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-160
 # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHzModeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
        Monitor         "IBM E74"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768_85"
        EndSubSection
EndSection
```

now i have a problem is that the login screen goes all the way to 1680 by something resolution.  can anyone fix my code to work for both to be 1024x768 at 85hz and 24 bit depth.
thanks

---

### Post by Clay_Banger on 2007-06-14
try changing:
```
                Modes           "1024x768_85"
```
to:
```
                Modes           "1024x768@85"
```
and changing:
```
# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHzModeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
```
to:
```
# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
Modeline "1024x768@85"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
```

---

