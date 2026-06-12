---
title: "3D Acceleration Not Working - iBook G4"
date: 2009-06-15
forum: Apple Hardware Users
---

### Post by billyjmc on 2009-06-15
I have an iBook G4 (mid-2005), aka powerbook6,7. It's the 12" 1.33GHz system. Try as I might, I cannot get the 3D acceleration to work on this system. Links: [_xorg.conf_]("http://billyjmc.freeshell.org/xorg.conf.txt"), _[lshw output]("http://billyjmc.freeshell.org/lshw.txt")_, _[Xorg.0.log]("http://billyjmc.freeshell.org/Xorg.0.log")_, and _[glxinfo output]("http://billyjmc.freeshell.org/glxinfo.txt")_. The astute reader will note that my Airport Extreme hardware isn't showing up; I've removed it, as it was malfunctioning, causing Mac OS X to lock up. After removing the card, the Mac OS X installer wouldn't run, since it no longer recognized my hardware as a genuine iBook configuration, I guess. :\ That's proprietary software for ya. So, after testing the waters with SuSE (KDE) & Fedora (Gnome), I made my way to Xubuntu. It's soo much more my style.

Anyway,I tried to follow the instructions from the _[community documentation]("https://help.ubuntu.com/community/RadeonDriver")_, but found that, contrary to what the site indicates, adding the code:
```
Option        "BusType" "PCI"
```to my xorg.conf actually causes glxgears (and other 3d apps) to _[lock up my computer]("http://ubuntuforums.org/showpost.php?p=7452501&postcount=8")_. Removing/commenting that line causes the sytem to behave normally (i.e. slow, but steady).

So far, I've [_compiled a new kernel_]("http://ubuntuforums.org/showthread.php?t=1145849"), and am running 2.6.30, with *uninorth-agp*, *agpgart*, and *radeon* now compiled as modules. I had tried to leave them hardcoded in the kernel, but I found that X11 comphttps://help.ubuntu.com/community/RadeonDriver=lained about not loading agpgart before radeon (from /var/log/Xlog.0.log):
```
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module is loaded before the radeon kernel module.
```So, I tried putting the modules in /etc/modules, which didn't solve anything. So, I _[blacklisted them]("http://ubuntuforums.org/showthread.php?t=304491")_ in /etc/modprobe.d/blacklist.conf. That also didn't work, so I _[rebuilt my initrd.img]("http://ubuntuforums.org/showthread.php?t=219600")_ to load the modules I need in the order listed above. (Of course, I put it in the /boot directory and adjusted the symlinks as needed.) This also did not work. I get the same message about loading modules in the wrong order.

And now, I have no idea what to do. Let's hear what you've got, wizards!

---

### Post by billyjmc on 2009-06-16
I have this mostly solved. I'm now getting sustained 1450+ fps with glxgears, so it's as good or better than what _[others have reported]("http://ubuntuforums.org/archive/index.php/t-462312.html")_. I still don't know why I had such a hard time getting it to work beforehand, though.

I ended up going to _[archlinuxppc.org]("http://www.archlinuxppc.org/")_, and they have a short _[wiki for the iBook G4 configuration]("http://wiki.archlinux.org/index.php/IBook_G4_12%22")_. There is good info there, so it's definitely worth checking out. Anyway, just for redundancy's sake, I've copied the new xorg.conf here, taken directly from their page. Even though the keyboard config says 'de', it's working fine for me, but you should probably double-check these to make sure they suit your system.
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen  0      "InternalScreen"
        InputDevice    "Synaptics" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0"    "SendCoreEvents"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Files"
        RgbPath      "/usr/share/X11/rgb"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/misc"
        FontPath     "/usr/share/fonts/100dpi"
        FontPath     "/usr/share/fonts/TTF"
        FontPath     "/usr/share/fonts/Type1"
        FontPath     "/usr/share/fonts/artwiz-fonts"
EndSection

Section "Module"
        Load  "glx"
        Load  "extmod"
        Load  "xtrap"
        Load  "record"
        Load  "dbe"
        Load  "dri"
        Load  "ddc"
        Load  "bitmap"
        Load  "int10"
        Load  "vbe"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel"   "xfree86"
        Option      "XkbLayout"  "de"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
       Identifier      "Synaptics"
       Driver          "synaptics"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "auto-dev"
       Option          "LeftEdge"              "50"
       Option          "RightEdge"             "840"
       Option          "TopEdge"               "30"
       Option          "BottomEdge"            "320"
       Option          "MinSpeed"              "0.2"
       Option          "MaxSpeed"              "1.5"
       Option          "AccelFactor"           "0.1"
       Option          "SHMConfig"             "on"
       Option          "RTCornerButton"        "3"
       Option          "LTCornerButton"        "2"
       Option          "FingerLow"             "12"
       Option          "FingerHigh"            "20"
       Option          "MaxTapTime"            "120"  
       Option          "HorizScrollDelta"      "15"
       Option          "VertScrollDelta"       "15"
       Option          "VertEdgeScroll"        "off"
       Option          "HorizEdgeScroll"       "off"
       Option          "VertTwoFingerScroll"   "on"
       Option          "HorizTwoFingerScroll"  "on"
EndSection

Section "Monitor"
        Identifier   "TFT"
        Option       "DPMS"
EndSection

Section "Device"
        Option      "AGPMode"                    "4"     
        Option      "AGPFastWrite"               "on"    
        Option      "GARTSize"                   "32"    
        Option      "RingSize"                   "8"
        Option      "EnablePageFlip"             "on"    
        Option      "AccelDFS"                   "on"
        Option      "UseFBDev"                   "false"  
        Option      "RenderAccel"                "true"
        Option      "SubPixelOrder"              "NONE"
        Option      "DynamicClocks"              "on"
        Option      "AccelMethod"                "EXA" 
        Option      "XAANoOffscreenPixmaps"      "true"
        Option      "BackingStore"               "true"
        Option      "ColorTiling"                 "on"
        Option      "MacModel"                    "ibook"  #important for dvi-out! 
        Identifier  "InternalDevice"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "M11 NV [FireGL Mobility T2e]"
        BusID       "PCI:0:16:0"
        Screen      0
EndSection


Section "Screen"
        Identifier "InternalScreen"
        Device     "InternalDevice"
        Monitor    "TFT"
        DefaultDepth      24

        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
                Virtual   2048 768
        EndSubSection
EndSection

```I realized after tweaking around a bit, that one of the problems I had was that I had set the GARTSize to 64, even through my card only has 32 megs of RAM. I thought for some reason that this would allocate additional memory from system ram for textures and whatnot. This is incorrect. Setting GARTSize too high results is abysmal performance. I've had a hard time finding documentation for what GARTSize is, exactly, and RingSize, too. Does anyone have any pointers on these? (I checked the radeon man page, of course.)

---

