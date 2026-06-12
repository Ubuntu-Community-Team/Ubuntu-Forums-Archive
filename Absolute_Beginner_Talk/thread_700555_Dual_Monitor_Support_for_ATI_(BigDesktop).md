---
title: "Dual Monitor Support for ATI (BigDesktop)"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by MC_LA on 2008-02-18
I'm a newbie to Ubuntu so any help will be greatly appreciated.  I'm trying to do something that you would think would be simply, but after several days of reading every post on the subject and doing exactly what they say, the best I can get is mirrored monitors.

Here's my info: 
I've got an Thinkpad T43p, ATI m24 GL [Mobility Fire GL V3200] (rev80)
running ubuntu 7.10
my external monitor is an old Impression monitor connected to the VGA of the Thinkpad docking station.

Below are the outputs from fglrxinfo, xrandr, aticonfig and xorg.conf.   I manually edited the xorg.conf since the aticonfig --initial is causing an null pointer exception and then deleting my xorg.conf.  

It seems odd that the aticonfig --query-monitor shows two monitors and the xrandr -q only shows one.   Why is that ?

running **fglrxinfo **gives me:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V3200
OpenGL version string: 2.0.6473 (8.37.6)
```

running **aticonfig --query-monitor** gives me:
Connected monitors: crt1, lvds
Enabled monitors: crt1, lvds

running **xrandr -q**gives me:
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 3200 x 1200
default connected 1280x1024+0+0 0mm x 0mm
3200x1200      60.0  
1280x1024      75.0     70.0     60.0*    50.0  
1400x1050      50.0  
1152x864       75.0     70.0     60.0     50.0  
1024x768       75.0     72.0     70.0     60.0     50.0  
800x600        75.0     72.0     70.0     60.0     56.0     50.0     47.0  
640x480        75.0     72.0     60.0     50.0  
1024x480       60.0  
848x480        60.0  
720x576        60.0  
720x480        60.0  
640x400        75.0     60.0     50.0  
640x350        50.0  
512x384        60.0     50.0  
400x300        75.0     60.0     50.0  
320x240        75.0     60.0     50.0  
320x200        75.0     60.0     50.0  
```

here's my **xorg.conf** minus the InputDevices:
```
Section "ServerLayout"
       Identifier     "Default Layout"
        Screen      0  "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
        Load  "GLcore"
        Load  "v4l"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        VendorName   "Plug 'n' Play"
        ModelName    "Plug 'n' Play"
        Gamma        1
        ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
        ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
        ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
        ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
        ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
        ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
        ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
        ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
        ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
        ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
        ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
        Identifier   "monitor1"
        VendorName   "Plug 'n' Play"
        ModelName    "Plug 'n' Play"
        Gamma        1
        ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
        ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
        ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
        ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
        ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
        ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
        ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
        ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
        ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsyn+vsync
        ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
        ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc M24GL [Mobility FireGL V3200]"
        Driver      "fglrx"
        BoardName   "ati"
        Option      "MergedFB" "off"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
        Option "DesktopSetup"  "horizontal" #Enable Big Desktop
        Option "Mode2"         "1280x1024" #Resolution for second monitor
        Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
        Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
        Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
        Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Device"
        Identifier  "device1"
        Driver      "ati"
        BoardName   "ati"
        Option      "MergedFB" "off"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc M24GL [Mobility FireGL V3200]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Virtual   1600 1200
                Depth     24
                Modes    "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1600x1200@60" "1152x864@75" "1024x768@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
        EndSubSection
EndSection

Section "Screen"
        Identifier "screen1"
        Device     "device1"
        Monitor    "monitor1"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "800x600@60" "832x624@75" "800x600@75" "1024x768@75" "800x600@72" "1024x768@70" "800x600@56" "1024x768@60" "640x480@75" "1152x864@75" "640x480@72" "1280x1024@75" "640x480@60" "1280x960@60" "1280x1024@60" "1280x960@75" "1400x1050@60" "1600x1200@60"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

---

### Post by Crooksey on 2008-02-18
[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)

enjoy

---

### Post by MC_LA on 2008-02-18
Thanks. Yes, I tried that one and a couple other threads too. The first post in that thread says if the aticonfig commands don't work, to modify the xorg.conf manually. For me, the aticonfig throws a null pointer exception so I did the manual recommendation. 

This is what's so frustrating is that i'm doing exactly what the posts say, but no matter I do, I never get past mirrored monitors.  

Is there something obviously wrong with xorg.conf or some other trick that I'm missing ?

---

### Post by MC_LA on 2008-02-22
Any ideas ?  or does Ubuntu simply not support dual monitors for ATI cards (other than mirrored) ?

to recap, I followed the post on BigDesktop (as best I could since I didn't always get the same results as expected, ie. aticonfig throwing null pointer exception) and the best I can get is mirrored monitors.

Does anyone else have a Thinkpad T43p (or similar) and have BigDesktop working ?  if so, can you please post what you did and maybe your xorg.conf ?  thanks.

---

### Post by sandusky1977 on 2008-04-03
I've got it up and running great, however I can't get the second monitor in the same resolution as the first. I'm Running View Sonic VG19" widescreens with a native res. of 1440x900 and I've got one running 1440x900 next two the other running 1024x768. I need help getting screen two in to 1440x900 for a true 2880x900.

Here is my xorg.conf Montir/Device Section
*******************************************************


Section "Monitor"
        Identifier   "Configured Monitor"
        Modeline "1440x900@70" 133.08 1440 1472 1976 2008 900 918 928 946
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "Mode2" "1440x900" #Resolution for second monitor
        Option      "Capabilities" "0x00000800"
        Option      "EnableMonitor" "tmds2i,tmds1"
        Option      "ForceMonitors" "tmds2i,tmds1"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection "Display"
                Virtual 1440 900
                Viewport   0 0
                Depth 24
        EndSubSection
EndSection


Anyone know what I'm doing wrong???

---

### Post by danaild on 2008-04-24
MC_LA, have you tried installing ati catalyst center?

I was stuck at the same position as you are (I had big desktop only on my login screen, after logon, I was able to see only cloned monitors), but after installing catalyst center, the big desktop worked (almost).

Unfortunately, after that I am not able to change the resolution of my second monitor to any greater than 1024x768.

If someone has any solution of that, pls answer.
(I have ati radeon x1600 video on HP 8430)

---

### Post by MC_LA on 2008-04-27
No, I didn't try catalyst center. I read enough issues with 7.10 that I decided to wait for 8.04 (Hardy)....well, I upgraded to 8.04 the other day, and with only an hour of messing around with the xorg.conf. I got dual monitors to work!

Unfortunately, 8.04 brought a bunch of new problems that I didn't have with 7.10. In addition to a bunch of smaller issues, the most annoying ones are synergy is now unusable and sleep/hibernate can't be recovered without restarting Xorg,

---

