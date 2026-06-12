---
title: "Solution: 1680x1050 resolution with Intel 82865G (i810 driver)"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Roo on 2007-10-01
I'm documenting this here to help others where I struggled to find the right information.

I have Ubuntu 7.04 (Fiesty Fawn) installed on an IBM PC with the following video card:
Intel Corporation 82865G Integrated Graphics Controller
My monitor is a Dell 2005FPW.

I'm fairly sure that anyone with the i810 graphics driver and a 1680x1050 LCD will hit the same problem.  To check if this is your problem - try the following:
```
grep i810 /var/log/Xorg.0.log 
```
You should see
> (II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),

and then this to check for the 1680x1050 failure
```
grep 1680 /var/log/Xorg.0.log
```
> (II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) I810(0): Not using mode "1680x1050" (no mode of this name)

_[COLOR="Red"]Solution[/COLOR]_

It is my understanding that there are two problems
[LIST=1]
[*]X11 doesn't do a great job detecting widescreen resolutions, so 1680x1050 isn't a choice in the config file
[*]The i810 driver doesn't support widescreen resolutions without some hackery
[/LIST]

To fix (1) - edit /etc/X11/xorg.conf
so your Screen section has 1680x1050 for each of the Mode lines.  The result will look similar to this (changes I made are in **bold**)
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "DELL 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           **"1680x1050"** "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           **"1680x1050"** "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           **"1680x1050"** "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           **"1680x1050"** "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           **"1680x1050"** "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes          ** "1680x1050"** "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

To fix (2) - follow the guide here.
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1)
This boils down to 
```
sudo apt-get install xserver-xorg-video-intel
```
edit /etc/X11/xorg.conf 
Change 
> Driver "i810"
to
> Driver "intel"

Now use CTRL-ALT-Backspace to cause X to restart.  You should now be in 1680x1050 mode.

Roo

---

### Post by Paulmd on 2007-10-02
Out of curiosity, why are you using the i810 driver on an i865? The i865 is a much newer, and better featured GPU.


Is there no proper linux driver for this chip?

---

### Post by xeta on 2008-03-14
Worked for me! Much thanks!

---

