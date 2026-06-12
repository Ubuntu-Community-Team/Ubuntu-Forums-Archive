---
title: "VirtualBox on a X server with custom res"
date: 2011-05-20
forum: Any Other OS
---

### Post by strike105x on 2011-05-20
Hi what i want to do is play some of my games using Virtual Box, the problem is that the max resolution of the games is 640X480 and at my current res doing it normally just results in a tiny window...so what i originally though was this (got the idea from a tut for starcraft on this forums):

Edit xorg.conf:

```
ection "ServerLayout"

# commented out by update-manager, HAL is now used
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Mouse0" "CorePointer"
    Identifier     "SCLayout"
    Screen      0  "StarCraft Screen" 0 0
EndSection

Section "Screen"
    Identifier "StarCraft Screen"
    Device     "aticonfig-Device[0]-0"
    Monitor    "StarCraft Monitor"
    DefaultDepth     24
    SubSection "Display"
        Virtual   640 480
        Depth     24
        Modes    "640x480@60" "800X600@60" (here (i mean where 800X600 is) was originally 1280X1024 but after the resolution used kept being 1280X1024@50 i tried tweaking a bit, but didn't do nothing)
    EndSubSection
EndSection

Section "Monitor"
    Identifier   "StarCraft Monitor"
    VendorName   "Plug 'n' Play"
    ModelName    "Plug 'n' Play"
    Gamma        1
    ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

```Then i made a script (based on the same starcraft tut) and run it:

```
#!/bin/sh
X :1 -layout SCLayout -ac &
XPID=$!
sleep 2
DISPLAY=:1 VirtualBox --startvm WindowsXP   -- /usr/bin/X :1 -layout SCLayout 
sleep 1
kill $XPID
```Problem is that like i said even the X server still used 1280X1024... Is what i'm trying to accomplish possible and if so what am i doing wrong ?

PS: my videocard is ati, i'm using the proprietary drivers and have linux mint 9 (based on ubuntu 9).

---

### Post by Perfect Storm on 2011-05-21
Moved to Other OS/Distro Talk.

---

### Post by strike105x on 2011-05-21
Okay i found out how to make virtualbox display 640X480 now all i need is to know how to start a custom X Server with the display of 640X480 please help.

---

