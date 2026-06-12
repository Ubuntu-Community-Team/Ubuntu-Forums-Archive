---
title: "Screen Resolution, Again"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by meisbored on 2007-02-05
OK, I was able to get my correct screen resolution before, but now that I have had to re-install Edgy I simply can not get it to allow me to change my resolution to the standard 1280x800 (widescreen) that I would have in Windows. I have tried editing xorg.conf, as well as reconfiguring xserver-xorg multiple times, and it just won't work no matter what I do. Does anyone have any ideas?

---

### Post by meisbored on 2007-02-05
Bump!

---

### Post by shareMenaPeace on 2007-02-05
Please post the hardware and model number aswell.

---

### Post by meisbored on 2007-02-05
HP Pavilion dv5000 (laptop)
Not sure what else you need to know hardware wise, like I said it worked before and I don't know why it's not working now...
Video card and all other stuff is standard Intel Chipset that came with the computer.

---

### Post by alienexplorers on 2007-02-05
Try this: GTF Modeline Generator "http://www.sh.nu/nvidia/gtf.php".
Just input your data into the boxes and hit Generate Modeline.
Take the data and install it in your xorg.conf file as so:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    ModeLine       "1024x768_85.00" 94.4 1024 1088 1200 1376 768 769 772 807 -hsync +vsync
    ModeLine       "1280x768_85.00" 118.5 1280 1368 1504 1728 768 769 772 807 -hsync +vsync
    ModeLine       "1280x960_70.00" 120.8 1280 1368 1504 1728 960 961 964 999 -hsync +vsync
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063 -hsync +vsync
    Option         "DPMS"
EndSection

Make sure you add in the screen section your resolutions selected in the modelines:

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1280x768" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1280x768" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1280x768" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1280x768" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1280x768" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1280x768" "1024x768"
    EndSubSection
EndSection

---

### Post by shareMenaPeace on 2007-02-05
> **alienexplorers said:**
> Try this: GTF Modeline Generator "http://www.sh.nu/nvidia/gtf.php".
Just input your data into the boxes and hit Generate Modeline.

Intresting, but how do i know my refresh rate?
Do you know a way to check this?

Currently i run a laptop nvidia card but it is only recoqunized as a default nvidia card.
But works ... even with beryl.

---

### Post by meisbored on 2007-02-05
I added a couple of modelines with different refresh rates, since I'm not sure which refresh rate I should use, but I still can't change it to anything other than 1024x768, 800x600, and 640x480, even though I removed those from the Display subsections in xorg.conf 
:confused:

---

### Post by meisbored on 2007-02-05
Can anyone help??

---

### Post by muzzamo on 2007-02-06
doing a search for "955resolution" might be what you are looking for. I know i have to use it to get widescreen working on my intel video powered laptop.

---

### Post by meisbored on 2007-02-06
I don't know what 955resolution is, nor can I find any information about it.

---

### Post by meisbored on 2007-02-06
Well I found something called 910resolution in the Synaptic Package Manager, and after installing it and reconfiguring xserver-xorg I was finally able to get the right resolution :D

---

### Post by muzzamo on 2007-02-06
Was about to say that

Yeah 855 resolution was what it was originally called, then it became 915.

Never 955 that was a typo on my part :-)

---

