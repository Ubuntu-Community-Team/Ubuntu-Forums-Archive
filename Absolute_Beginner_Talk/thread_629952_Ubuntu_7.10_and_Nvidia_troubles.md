---
title: "Ubuntu 7.10 and Nvidia troubles"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by danthegeek on 2007-12-02
I am new to Ubuntu and Linux in general.  I was wondering if anyone could help out a newb?

Anyways,  I have been trying to install the Nvidia drivers and have had no luck.  I turn off X and install the drivers but, when I start X back up I get a message saying something like "Unable to detect your video card and resolutions."  It gives me a box to configure it myself.  I guess I need to adjust the config file for it but i have no idea how.  I also get no Nvidia logo on boot of X.  I know the card works fine because I have been using it with Windows for a while.  The card is an 8800gt if that helps, and ive been installing the beta drivers 169.04.   Can anyone please help, Ive been trying for 4 days lol.

-dan

---

### Post by overdrank on 2007-12-02
> **danthegeek said:**
> I am new to Ubuntu and Linux in general.  I was wondering if anyone could help out a newb?

Anyways,  I have been trying to install the Nvidia drivers and have had no luck.  I turn off X and install the drivers but, when I start X back up I get a message saying something like "Unable to detect your video card and resolutions."  It gives me a box to configure it myself.  I guess I need to adjust the config file for it but i have no idea how.  I also get no Nvidia logo on boot of X.  I know the card works fine because I have been using it with Windows for a while.  The card is an 8800gt if that helps, and ive been installing the beta drivers 169.04.   Can anyone please help, Ive been trying for 4 days lol.

-dan

HI and welcome, have you tried envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by GSF1200S on 2007-12-02
Did you try the restricted drivers manager? I tried for a while getting my geforce 7600 to go with the website drivers, but at least on 7.10, I kept running into kernel source errors.

Ive heard the 8800 series has a few issues to work through, so im not sure I can help... The restricted drivers manager worked for me, and im on KDE to boot!

---

### Post by danthegeek on 2007-12-02
I have tryed Envy with no change.  the drivers will install and I get the same message and no Nvidia Logo.  When i try the Restricted drivers manager it gives me a message saying "your hardware does not need restricted drivers" or something similar.  ???

---

### Post by Hospadar on 2007-12-02
try using envy and to the "remove" and "clean" options
then try using the restricted driver manager

---

### Post by GSF1200S on 2007-12-02
Post the results of:

lspci


Is something nvidia listed in there? I dont think ive ever seen a problem like this one...

---

### Post by danthegeek on 2007-12-02
This is what I get for lspci  > dan@dan-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
dan@dan-desktop:~$ 


??

---

### Post by danthegeek on 2007-12-02
> **Hospadar said:**
> try using envy and to the "remove" and "clean" options
then try using the restricted driver manager

I tried it and got the same message of "your hardware blah blah."

Thanks for the help again, I rely want to get this working.  Im tired of 800X600 res.

---

### Post by danthegeek on 2007-12-02
OK I have some good and bad news.  First the good news.

I threw in an old 7800gt from my sli rig and I installed the drivers just fine and I can actually adjust the res lol.  ENVY is King

The bad news.  No matter what I try I can not get the 8800gt to install in ubuntu.  It just does not recognize the 8800gt in Ubuntu.

---

### Post by GSF1200S on 2007-12-02
> **danthegeek said:**
> OK I have some good and bad news.  First the good news.

I threw in an old 7800gt from my sli rig and I installed the drivers just fine and I can actually adjust the res lol.  ENVY is King

The bad news.  No matter what I try I can not get the 8800gt to install in ubuntu.  It just does not recognize the 8800gt in Ubuntu.

hmmm.. I know for awhile people were having problems with the 8800gt, but they seem to be resolved. Ill do a little sniffing and see what I can find. In the mean time, do me a favor- post your xorg.conf with the nvidia 8800gt drivers installed.

To do this, throw the 8800gt back in, kill x, reinstall the drivers, and attempt a reboot. Of course it will prolly fail. When it does, load the liveCD, and open the xorg.conf:

sudo gedit /etc/X11/xorg.conf

Post your xorg.conf.. maybe we can manually input what is missing and get you up and rolling.. Do you tell the nvidia xconfig to automatically update the xorg.conf? Either way, post it here so we can look at it. Even if I cant help, maybe someone else can..

---

### Post by danthegeek on 2007-12-03
This is what I get

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov 14 17:10:54 PST 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Acer"
    ModelName      "Acer AL1916W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1680x1050@75" 188.1 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"

 #  
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 #  
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1440x900@75" "1440x900@60" "1280x800@60" "1600x1024@60" "1280x768@75" "1680x1050@60" "1280x800@75" "1680x1050@75" "1280x720@60" "1920x1200@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

 #  
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

I got the 8800gt working but when I restart the system it returns to low graphics mode.  I saw a similar problem but i dont remember the fix for it.  Dont even ask how I got it working. I just installed the drivers again and BAM.  It works.  I just dont want to have to install the drivers everytime I boot it up.  Thanks agin for the help.

-dan

---

### Post by GSF1200S on 2007-12-03
> **danthegeek said:**
> This is what I get



I got the 8800gt working but when I restart the system it returns to low graphics mode.  I saw a similar problem but i dont remember the fix for it.  Dont even ask how I got it working. I just installed the drivers again and BAM.  It works.  I just dont want to have to install the drivers everytime I boot it up.  Thanks agin for the help.

-dan

Its returning to low graphics mode because of failsafe X, which will revert to nv drivers when X fails on the nvidia drivers. 

This may seem like an off the wall question, but how do you connect to the internet? If you use wireless, this could get tough. If not, then it should be a simple fix.

Since it works once when you restart X, and then fails on reboot, try this.. Install the drivers, and startx. Once X is loaded, open up synaptic and do a search for "nvidia common kernel." Once it finds it, remove the common kernel, and try a reboot- it should work. Back in the day before failsafe X, if X failed for me it was due to an API mismatch error between the nvidia drivers and the nvidia common kernel. Of course, you wouldnt see that message because it automatically reverts to nv drivers.

Give it a shot and report back.. good luck :)

---

### Post by danthegeek on 2007-12-03
THANK YOU SO MUCH.  IT WORKED  :guitar:


Ok, im fine now.  I did exactly what you said and did a complete removal and I now have a working 8800gt and 1440x900 res. THANK YOU.  It looks like I cant give up on Linux yet.

-dan

---

### Post by GSF1200S on 2007-12-03
> **danthegeek said:**
> THANK YOU SO MUCH.  IT WORKED  :guitar:


Ok, im fine now.  I did exactly what you said and did a complete removal and I now have a working 8800gt and 1440x900 res. THANK YOU.  It looks like I cant give up on Linux yet.

-dan

Hell yeah!! Good to hear- Linux lives on in your computer ;)

---

