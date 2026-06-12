---
title: "External LCD Display (Native 1400x1050) does not do 1400x1050"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by haelters on 2007-07-22
I'm getting quite desperate... I have a Thinkpad X60 tablet edition with a 1400x1050 internal LCD screen. While I'm using that, everything is great.

However, when I want to use my External Samsung 203B screen (also a native 1400x1050 LCD) it simply does not work correctly. It tries to put 1400X1050 on the external screen, but the bottom panel isn't visible anymore. So it missing about 24px. The width is correct.

I've tried other resolutions on the external screen and they all give a correct result. However since on a LCD the native resolution gives the best result, I want to have 1400x1050.

Meanwhile, I've also installed RandR 1.2. Again everything is working correctly EXCEPT the thing I need ... A correct 1400x1050 on both screens.

I also tried to use both the I810 and the intel driver, but both give the same problem.

When I look at the OSD, the External screen says that it is doing 61.7kHz, 57Hz PN. When I use my Desktop PC it shows 65.3kHz, 60Hz, NP.

Since I thought it might be a timing problem, I've tried to add a modline, but it does not work (could be I'm doing it wrong).

I really have no clue how to continue, so any help is appreciated !




----------------- Output of different info commands & configs ------------------------
ii  xserver-xorg-video-intel              2.0.0-1feisty1                        X.Org X server -- Intel i8xx, i9xx display driver
ii  xorg                                  7.2-0ubuntu11                         X.Org X Window System
ii  xserver-xorg-core                     1.3.0.0.dfsg-1feisty1                 X.Org X server -- core server (updated but original gave the same problems)


The output of RandR:
manfred@manfred-x60t:~$ xrandr -q
Screen 0: minimum 320 x 200, current 2800 x 1050, maximum 2800 x 2800
VGA connected 1400x1050+1400+0 (normal left inverted right) 408mm x 300mm
   1400x1050      60.0*+   60.0  
   1280x1024      59.9  
   1280x960       59.9  
   800x600        56.2  
   640x480        60.0  
LVDS connected 1400x1050+0+0 (normal left inverted right) 245mm x 184mm
   1400x1050      50.0*+
   1280x1024      59.9  
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0     59.9  
TV disconnected (normal left inverted right)

-------------------------------------- xorg.conf extract ----------------------
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "Intel 1"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "Intel 2"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
        Modeline "1400x1050" 121.75  1400 1488 1632 1864  1050 1053 1057 1089
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 1"
        Monitor         "Laptop Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
                Virtual         2800 2800
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "Intel 2"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

---

### Post by JustAboutRealJAR on 2007-07-23
Try another method of dual monitor setup. Merged FB worked for me...

All four methods are listed here (though I think you've probably been to this link since you managed to set it up with the xinerama method):

[http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

let me know how this works out for you

---

### Post by JustAboutRealJAR on 2007-07-23
it just occured to me that your graphics card may not be able to handle such high resolutions on 2 monitors. Perhaps the issue is a limitation of the graphics card.

to test this... try setting the laptop screen to a lower resolution to free up resources. Once you have that working, set the external monitor the higher resolution and see if it works that way.

It would suck if this was the issue: laptop graphics cards are very hard/impossible to upgrade

---

### Post by haelters on 2007-07-23
Windows is able to do this resolution. Even with my laptop screen completely disabled I still have these issues.

---

### Post by haelters on 2007-07-27
when I try to put the external screen into 1680x1050 with xrandr:

xrandr --output VGA --mode 1680x1050

the OSD of the tft panel says that it is doing 1400x1050 at 65.3kHz, 60Hz NN... What mode must I patch with 915resolution ??? Do I have to do something else ?

I'm really getting desperate here !

---

