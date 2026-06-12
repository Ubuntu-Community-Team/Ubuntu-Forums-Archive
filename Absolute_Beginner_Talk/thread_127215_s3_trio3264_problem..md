---
title: "s3 trio32/64 problem."
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-02-08
i installed ubuntu and when it got to loadin or rather starting ubuntu.... my monitor went blank, good thing i have a spare Hard drive with winxp on it. hope you guys can help me, can i use s3 trio32/64 on ubuntu or any other linux os? thanks a lot.

---

### Post by Leif on 2006-02-08
I have one, and it works just fine. try booting into secure mode, then run "sudo dpkg-reconfigure xserver-xorg". the relevant parts of my xorg.conf look like this :

```

Section "Device"
       Identifier      "S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]"
       Driver          "s3"
       BusID           "PCI:0:5:0"
EndSection

Section "Screen"
       Identifier      "Left Screen"
       Device          "S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]"
       Monitor         "Dell"
       DefaultDepth    16
       SubSection "Display"
               Depth           1
               Modes           "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           4
               Modes           "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           8
               Modes           "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           15
               Modes           "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           24
               Modes           "1280x1024" "1024x768" "800x600" "640x480"
       EndSubSection
EndSection

```

---

