---
title: "Trying to set up duel montiors with Nvidia 8800"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by sainin2 on 2008-01-23
So iv had ubuntu for 2 days now. Iv been attempting to set up my monitors like i had them bak in windows but cant seem to figure it out. I have a Nvidia 8800 graphics card with 2 monitor output (VGA i think there called) and hooked up. Iv installed a driver i got from  a nvidia forum using envy (169.09). Using the NVidia menu and many forums i have come to the setting i think may possibly work.  But this is where im completly lost. When i click the save to x configuration file, and tell it to merge with /ETC/X11/xorg.conf and click save i get a unable to create new x config back up file /etc/X11/xconf.backup. When i click apply sometimes i get a metamode error saying 2 metamodes are the same and they gotta be differnt or it tells me it cant complete all changes unless i save it to xconf and restart xserver. Well i cant save it to xconf and i dont no how to restart xserver. I was feeling risky and try gedit /etc/X11/xconf  ( something i semi lrned while installing driver) but wen i click save it said i wasnt allowed  and im admin ( mind u that could be a good thing i dunno). So.. any ideas on where i went wrong or wat to do next

---

### Post by smurphy_it on 2008-01-23
Try to following.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

Always good to have a backup!.

To restart the X-server, hit Ctrl-Alt & backspace.

---

### Post by sainin2 on 2008-01-23
lol u dont wanna no what i just did and i dont no how i some how got out of it but anyways. I seem to be on the right track. My current main issue is wen i click apply in theNvidia options i got some metamode13 is the same as metamode 3.  How can i fix this?

Btw thx for ur help. Your coding works smurphy and i manage to change my xorg.conf.
And yes ur right its a good thing to have backups. When i copyed the preveew of wat i was trying to save in xorg.conf into it i got what seemed like my offscreen but nothing came on my main screen. (How ever i did tell it to delete some metamodes which may have caused it)

---

### Post by Perfect Storm on 2008-01-23
Have you tried setting it up via

```
gksudo nvidia-setting
```

---

### Post by sainin2 on 2008-01-23
so i typed in the gksudo nvidia-setting. It asked for my password but noticibly did nothing. what was that suppose to do??


Edit: When i enter my Nvidia settings now i only see one monitor option not both =(  *Found the other one

---

### Post by Perfect Storm on 2008-01-23
You can't see the password you're typing

---

### Post by sainin2 on 2008-01-23
ohh sry my bad i wasnt too clear. When it asked for my password i typed it in. After that no new lines came up, no windows opened. From what i can tell it seems to turn my monitors off when i go to the nvidia settings but thats all i can see

---

### Post by sainin2 on 2008-01-23
Well i got it working. Thanks for all your help guys. Not too sure what i changed but those errors stopped coming and its working nicly. Maby ubuntu really is better then windows =)

---

### Post by sainin2 on 2008-01-25
Well i thought i had it workng. Currently I have my 2 screen running. My main monitor is a samsung syncmaster 940NW and my off one is a nokia 447ziPLus (one big ugly old mamoth monitors) Now i want to use a 1440 resolution on my syncmaster and a 1024x786 on the nokia. So far it wont let me do this. Usually wen i try and set them up right my screens go crazy and flash like red line accross it(not sure how else to describe it). With this setting my main screen does this. My guess is this is due to overlapping screens, although i dont no how to fix this

Im not sure if im coming out very clear but any questions or suggestions let me no =)

---

### Post by Perfect Storm on 2008-01-25
Though duel monitors is not my specialties, let see how your xorg.conf looks like;

```
cat /etc/X11/xorg.conf
```

---

### Post by sainin2 on 2008-01-25
Here it is, but i dont no how to put it into one of the boxes but ill try this and see what happens

[PHP]Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1024 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "vbe"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
# Removed Option "Xinerama" "true"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 940N,SyncMaster Magic CX915N/CX916N/CX917N"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
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
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
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
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "NOKIA 447Zi+"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 150.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1440x900@60" "1600x1024@60" "1440x900@75" "1680x1050@60" "1280x800@60" "1920x1200@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

        # Removed Option "TwinView" "1"
        # Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1440x900@75 +1024+0; CRT-0: nvidia-auto-select +0+0, CRT-1: 1440x900@60 +1024+0; CRT-1: 1440x900@75 +0+0; CRT-1: 1280x800@60 +0+0; CRT-1: 1280x768@75 +0+0; CRT-1: 1280x800@75 +0+0; CRT-1: 1280x720@60 +0+0; CRT-1: 1280x768@60 +0+0; CRT-1: 800x600@60 +0+0; CRT-1: 800x600@75 +0+0; CRT-1: 800x600@72 +0+0; CRT-1: 800x600@56 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: 1440x900_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection[/PHP]

basically since i wasnt sure what i was doing, and i knew my Nvidia setting was trying to save but complaining about not being able to make a back up i would copy and paste the preview

---

### Post by Perfect Storm on 2008-01-25
Found this: [http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitor](http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitor)

---

