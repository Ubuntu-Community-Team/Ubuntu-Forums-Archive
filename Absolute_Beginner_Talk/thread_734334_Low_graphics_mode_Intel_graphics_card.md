---
title: "Low graphics mode Intel graphics card"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by mxwf on 2008-03-24
Hi everyone, I installed 7.10 on a GatewayMX6901m laptop a few days ago, and I have tried a couple of things to get my Graphics card (Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller) running, but with no results. Every time I reboot I get a message that says: Unable to detect card, you need to reconfigure it manually. 

I've tried to reconfigure xorg:  sudo dpkg-reconfigure xserver-xorg

I've also tried installing 915 driver and then editing the text file.

I've also created a patch with another mode on 915, and still the same.

I don't know if this is enough information, if it isn't please let me know. I'm a bit frustrated. I appreciate your help.

---

### Post by moore.bryan on 2008-03-24
have you followed the reconfigure in [this]("http://ubuntuforums.org/showthread.php?t=690760") thread?

---

### Post by mxwf on 2008-03-24
Yes Sir, that was the first one I tried. Even after restarting X, I didn't get 1200 x 800 and I wasn't able to enable desktop effects.

---

### Post by moore.bryan on 2008-03-24
could you post your xorg.conf?
```
cat /etc/X11/xorg.conf
```

---

### Post by mxwf on 2008-03-24
Here it is, thank you very much!

Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "Intel 915"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 640     480
                Modes           "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "Intel 915"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  1
        Vendorname      "Intel"
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
EndSection
Section "device" # 
        Identifier      "device2"
        Boardname       "Intel 915"
        Busid           "PCI:0:2:1"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection
Section "screen" # 
        Identifier      "screen2"
        Device          "device2"
        Defaultdepth    24
        Monitor         "monitor2"
EndSection
Section "monitor" # 
        Identifier      "monitor2"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by moore.bryan on 2008-03-24
from what you've posted, your monitor has been set to the failsafe mode.

when you ran the reconfigure, how did you answer the video card questions?

also, try installing xserver-xorg-video-intel:
```
sudo aptitude install --with-recommends xserver-xorg-video-intel
```

---

### Post by mxwf on 2008-03-25
Hi, back from work. OK when I tried this:
```
sudo aptitude install --with-recommends xserver-xorg-video-intel
```
this came up:

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Then, I answered this for the configuration:

Attempt to autodetect video hardware? Yes
X server driver: Intel
Identifier for your video card: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
Video card's bus identifier: PCI:0:2:0
Amount of memory (kB) to be used by the video card: 393216
Use kernel framebuffer device interface? No
Attempt monitor autodetection? Yes
Identifier for the monitor: Generic Monitor_
Video modes to be used by the X server: 1280 x 800 
Method for selecting the monitor characteristics: Simple
Approximate monitor size: 15 inches (380 mm)     (My monitor's size is 15.4")

Now, my computer's graphic specs are this:

Display panel 	15.4-inch WXGA (1280 × 800)
Video controller  Intel Graphics Media Accelerator X3100 up to 384 MB of Dynamic Video Memory 

So here it is. I hope this helps.

---

