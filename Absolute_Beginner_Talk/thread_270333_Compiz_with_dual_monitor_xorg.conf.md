---
title: "Compiz with dual monitor xorg.conf"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-10-03
Hey all,
I am using this how-to [http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036) in order to install beryl

I have a dual monitor setup using twinview

Here's the device section of MY xorg.conf

Section "Device"
        Identifier "twinview"
        VideoRam 128000
        VendorName "nVidia Corporation"
        BoardName "Video device"
        Driver "nvidia"
        BusID "PCI:2:0:0"
        Screen 0
        Option "TwinView"
        Option "MetaModes" "1600x1200,1600x1200"
        Option "TwinViewOrientation" "LeftOf"
        Option "SecondMonitorHorizSync""UseEdidFreqs"
        Option "SecondMonitorVertRefresh" "UseEdidFreqs"
        Option "HWCursor" "On"
        Option "UseEdidFreqs" "true"
        Option "NvAGP" "1"
        # Option "NoLogo" "true"
        # Option "RenderAccel" "true"
        # Option "CursorShadow" "true"
        # Option "XvmcUsesTextures" "true"
EndSection

In the how-to he wants me to change the values to look like this:

Section "Device"
Identifier- leave this line alone!
Driver "nvidia”
BusID “PCI:1:0:0&#8243;
Option “RenderAccel” “true”
EndSection

Do I change the BusID on my xorg.conf, im not sure what the BusID is?
Can I just add the Option "RenderAccel" "True" to my xorg.conf since everything else looks the same but the BusID and the Option.

---

