---
title: "screen shrunken and duplicated"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by greengolftee87 on 2009-04-26
I have tried successfully several times to install ubuntu ppc on my Ibook with the exception of 1 thing. it thinks the screen is like 2/3 the size that it really is.  the right 3 inches are all black and the bottom 3 inches are a mirror of the top with a small discolored break inbetween. 

Also i cannot change the resolution through system prefs or the command line.

[IMG]http://img.geocaching.com/cache/5056087d-0aa3-49ab-8a96-6d36f4d8e248.jpg[/IMG]

---

### Post by stream303 on 2009-04-27
I don't know what version you are running, but you may have to manually edit your /etc/X11/xorg.conf file, and perhaps force the resolution with something like this (assuming 1024x768 )

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth     24
           SubSection       "Display"
             Depth            24
             Modes            "1024x768"
           EndSubSection
EndSection
```

---

### Post by moocow1452 on 2009-04-27
I concur, but my laptop's a G3 too, and this is my Xorg.conf

```
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```

Copy/Paste into that file with gedit, restart, and you should be good to go.

---

### Post by stream303 on 2009-04-27
Well, right off it looks like you are using the horizontal and vertical freqs that are spec'ed for G3 iMacs, and not iBooks!

I'd have to check around to see what the iBook specs for H and V are, and unfortunately, I'm not savvy with ATI.

Although the first thing I'd try is giving yourself a little leeway by changing 60-60 to 58-62, but I'd look into seeing where the ibooks values are different from the iMacs..

---

### Post by moocow1452 on 2009-04-27
> **stream303 said:**
> Well, right off it looks like you are using the horizontal and vertical freqs that are spec'ed for G3 iMacs, and not iBooks!

I'd have to check around to see what the iBook specs for H and V are, and unfortunately, I'm not savvy with ATI.

Although the first thing I'd try is giving yourself a little leeway by changing 60-60 to 58-62, but I'd look into seeing where the ibooks values are different from the iMacs..
I got the sync info from [here,]("http://ubuntuforums.org/showthread.php?t=1114297") and it's been working ok...

---

### Post by stream303 on 2009-04-27
Aha!  So is it working now?

Here's another one for the G3 iBook that uses some different values - perhaps certain versions of the ibooks like these better?

[http://reversemidastouch.blogspot.com/2007/05/edubuntu-install-ibook-g3.html](http://reversemidastouch.blogspot.com/2007/05/edubuntu-install-ibook-g3.html)

Essentially he is using a Horizontal of 28-51, and a Vertical of 43-60 (along with some older config info)

---

### Post by greengolftee87 on 2009-04-27
Got it working by adding the sync values, You guys are great, Thanks so much

---

