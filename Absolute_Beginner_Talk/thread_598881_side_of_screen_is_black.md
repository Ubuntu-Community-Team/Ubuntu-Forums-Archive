---
title: "side of screen is black"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by achoi02 on 2007-10-31
problem:
the correct resolution is set 1440x900 60khz (19" lcd)
however, the left side of the screen is blank and the rest of the screen is squished, as show on the picture. so it almost looks like the screen has turned into a 4:3 screen or maybe 5:4 

earlier, i got it to 1280x768 and i was going to settle but now i can't even set it to that. i remember i had this problem w/ the computer when i first got it  (dell e520n ship w/ 7.04). so i'd have to change the refreshrate from 75 to 60 khz and that fixed it back then. 

i have a g965 chipset and a norcent 19" LCD on 7.10 amd64

tried searching the forums for solution but  =*(
i'm crazy about aspect ratio and resolution so this is driving me nuts X_X

---

### Post by alwiap on 2007-10-31
i had the same problem with my 1440x900 monitor but i changed it by going into Screen and Graphics Preferences and manually changing the values to:
```
LCD Panel 1440x900 (widescreen)
Resolution 1440x900 @ 50 Hz
```

i assume you tried that and it didn't work?

---

### Post by overdrank on 2007-10-31
> **achoi02 said:**
> problem:
the correct resolution is set 1440x900 60khz (19" lcd)
however, the left side of the screen is blank and the rest of the screen is squished, as show on the picture. so it almost looks like the screen has turned into a 4:3 screen or maybe 5:4 

earlier, i got it to 1280x768 and i was going to settle but now i can't even set it to that. i remember i had this problem w/ the computer when i first got it  (dell e520n ship w/ 7.04). so i'd have to change the refreshrate from 75 to 60 khz and that fixed it back then. 

i have a g965 chipset and a norcent 19" LCD on 7.10 amd64

tried searching the forums for solution but  =*(
i'm crazy about aspect ratio and resolution so this is driving me nuts X_X

Hi and this link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
If you need more help you can post  the output of this command in the terminal ```
cat /etc/X11/xorg.conf
```

---

### Post by achoi02 on 2007-10-31
> **alwiap said:**
> i had the same problem with my 1440x900 monitor but i changed it by going into Screen and Graphics Preferences and manually changing the values to:
```
LCD Panel 1440x900 (widescreen)
Resolution 1440x900 @ 50 Hz
```

i assume you tried that and it didn't work?

50 HZ? i'm unable to set it 
for 1440x900 i only get 60 and 75 hz and 75 is out of range

i think i got it to 54hz or so once and it was really screwed up, it only showed part of the screen and the mouse pointer was like 200 pixels off from where it clicked ???

---

### Post by achoi02 on 2007-10-31
> **overdrank said:**
> Hi and this link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
If you need more help you can post  the output of this command in the terminal ```
cat /etc/X11/xorg.conf
```

i've tried the link but the problem is i can't find the vert hori refreshrates from the manufacture website b/c the specifications pdf is corrupt and and the manual that came w/ it doesn't include the information. 

anyways i just played around w/ it and right now i got it working w/ 1280x768 but i'd definitely prefer the native resolution 


```
 Section "Device"
        Identifier      "Intel Corporation 82G965 Integrated Graphics Controller"
        Boardname       "intel"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "JT198xB"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82G965 Integrated Graphics Controller"
        Monitor         "JT198xB"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1440x900@75"   "1440x900@60"   "1280x800@60"  "1600x1024@60"   "1280x720@50"   "1680x1050@60"  "1280x768@75"   "1680x1050@75" "1280x800@75"    "1920x1200@60"  "1280x720@60"   "1280x768@60"   "1280x854"     "1152x768@54"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "intel"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  1
EndSection
Section "screen" # 
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" # 
        Identifier      "monitor1"
        Gamma   1.0

```

---

### Post by overdrank on 2007-10-31
Ok if it were I, have you tried and change anything in the screen and graphics under system, administration? If all else fails open a terminal and use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Good luck! :KS

---

### Post by achoi02 on 2007-11-24
yeah i never found the fix for this, 
it especially was bothersome since i couldn't download the spec sheet from the manufacturer's website. also, the 1440x900 may be a particularly difficult resolution.

i gave up on it and got a new monitor. sometimes, it's not worth the extra hrs to try to fix it when u know it'll probably work on a different configuration. 

for the record, the westinghouse LCM22w3 has no issues.

---

### Post by inportb on 2008-01-13
Darn, I have this problem too. Is there a solution?

---

