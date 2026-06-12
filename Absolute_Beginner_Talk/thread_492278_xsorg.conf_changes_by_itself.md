---
title: "xsorg.conf changes by itself"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Ilan Shalif on 2007-07-04
I use Kubuntu 
It already happened twice that my xorg.conf was changed and the resolution changed from 1600X1200 into "640x480@60" while the original was changed into xorg.conf.1 

Section "Monitor"
        Identifier      "Q995"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "Q995"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection


changed into:
Section "Monitor"
  identifier "Q995"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

I discovered it when I booted the computer and replaced the new one with the old one and rebooted to get the correct resolution.

I wonder what change my xorg.conf

---

### Post by TheRingmaster on 2007-07-04
Did you recently install a graphics driver?

---

### Post by Ilan Shalif on 2007-07-04
> **Ilan Shalif said:**
> I use Kubuntu 
It already happened twice that my xorg.conf was changed and the resolution changed from 1600X1200 into "640x480@60" while the original was changed into xorg.conf.1 

Section "Monitor"
        Identifier      "Q995"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "Q995"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection


changed into:
Section "Monitor"
  identifier "Q995"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

I discovered it when I booted the computer and replaced the new one with the old one and rebooted to get the correct resolution.

I wonder what change my xorg.conf


I now recal that I tested changing the gama from 1.0 into 2.0.... and than back to 1.0 - may be this caused the replacement of xorg.conf ?

---

### Post by Ilan Shalif on 2007-07-04
> **TheRingmaster said:**
> Did you recently install a graphics driver?

I do not recall installing any graphic driver, but may be it was included in one of the packages.

However, checking the other versions of  xorg.conf - of the previous days and I found that the previous problem was related to gamma too:
2007-06-28 17:33 tmp/xorg.conf-orig
Section "Monitor"
  identifier "Q995"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies Inc RV280 [Radeon 9200 SE]"
  Monitor "Q995"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

---

