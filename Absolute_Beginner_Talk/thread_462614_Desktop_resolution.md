---
title: "Desktop resolution"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-02
I have installed ubuntu 6.10 and then updated to 7.04.  This seems to have allowed me to get my wireless working.  I have a Gateway MX3215 laptop and it uses a Gateway Via S3 driver for the video in Windows (in case that helps in this question).  When I boot from the live cd, my screen resolution is higher than after I have installed from it.  In addition, the desktop area between the top system bar and the lower system bar is sized larger than the physical screen, so I can't get to such things as the "X" box in the upper right of a window, etc..  The hardware manager in LInux show my video as Unichrome Pro IGP, so I used the package manager to install the unichrome package.  The notes for that package (in the package manager screen) said that since "via" already existed in X, they were calling the module "unichrome".  So, once package manager finished I did an sudo gedit /etc/X11/xorg.conf and changed the device type to "unichrome".  As soon as I do the ctrl-alt-backspace to restart X, it aborts and in the logs it says it can't find "unichrome".  Can someone tell me what I need to do to set up X as unichrome and get my resolutions (hopefully) straightened out?

Thanks:p

---

### Post by Happy_Man on 2007-06-02
Reset it to vesa..... and then try to change the resolution.

---

### Post by gcos7 on 2007-06-02
;)I checked the default xorg.conf file that I restored after trying unichrome, and it does say vesa.  When I try to change resolutions via system/preferences/screen resolution, the only options are 800x600 and 600x480.  In addition, if I try to change it from the default of 800x600, the screen looks all screwy and after the 40 seconds it comes back and I get to select to keep my old resolution.  Any thing else I can check?:p

---

### Post by Happy_Man on 2007-06-03
There will be a section that looks like this... (mine's here as an example):

> Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 420]"
        Monitor         "DELL E171FPb"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
EndSection

D'you see where I have all the resolutions? You probably don't have as many. Edit your xorg.conf so that it does have whatever resolutions you need in the sections, and then log out, and log back in. Then see whether you can change the resolution. *FYI: I'm using vesa too, and I get 1280x1024 easily.*

---

