---
title: "Video Driver Problems"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by lorderico on 2008-03-11
I am using a radeon 9600 video card.  I first installed the driver Ubuntu came with, it worked fine.  Then I tried to get a driver made by ATI because I thought It would give me extra desktop effects.  That did not turn out well, as it brought Ubuntu back to looking "classic" (top and bottom bars gray, weird icons).  So I stopped using the ATI video driver, and now the resolution I want (1024 x 768) is not available).  This causes either a. too small of writing or b. the bottom bar doesn't show on the screen.

Thanks

Eric

---

### Post by Rocket2DMn on 2008-03-11
Assuming it worked OK (everything was detected automatically) after you installed, you can restore your original graphics settings with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE

---

### Post by lorderico on 2008-03-12
I tried it, but it didn't do anything.

---

### Post by Rocket2DMn on 2008-03-12
OK, why don't you try reconfiguring it manually then by not using the phigh flag (you will get asked a bunch of questions, do your best to answer).  You will want to the "ati" driver since it offers Accelerated 3D Support for your card (not full support, but still good).  You will also be able to select your screen resolution - choose your monitor's max and everything less.

---

### Post by lorderico on 2008-03-12
Accidentally posted here.

---

### Post by lorderico on 2008-03-12
Please help, I did what you said, but must have done something wrong.  Now the resolution is still wrong.  Now my visual effects don't work (compiz effects).  I would at least like to have it back the way it was.

---

### Post by lorderico on 2008-03-12
ok, I got the resolution to work, now I just need to get the desktop effects back...

---

### Post by Rocket2DMn on 2008-03-13
Can you please post your xorg.conf file?
```
cat /etc/X11/xorg.conf
```
Also, how many FPS do you get when you run
```
glxgears -info
```

---

### Post by lorderico on 2008-03-13
Section "Files"
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc M10 NQ [Radeon Mobility 9600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M10 NQ [Radeon Mobility 9600]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

8424 frames in 5.0 seconds = 1668.173 FPS
8634 frames in 5.0 seconds = 1712.369 FPS
9000 frames in 5.1 seconds = 1781.801 FPS
8880 frames in 5.0 seconds = 1763.422 FPS
8971 frames in 5.0 seconds = 1781.948 FPS

Thanks for your help,
Eric

---

### Post by Rocket2DMn on 2008-03-13
Your xorg.conf file looks fine and you're getting great FPS, you should be able to enable desktop effects.  Try running
```
compiz --replace
```
You can customize your effects from System->Preferences->Advanced Desktop Effects Settings.  You should first enable Compiz Fusion from System->Preferences->Appearance, Visual Effects tab.

---

### Post by lorderico on 2008-03-13
I tried it and this is what I got:

leo@Ebuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e51 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

leo@Ebuntu:~$ 

(I got tired of waiting after "aborting and using fallback: /usr/bin/metacity" didn't go away after a few minutes, so I figured it wasn't going to work and pressed control c)

Thanks for the help

---

