---
title: "X-server to Screen Resolution"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-14
Ok so last night I was having troubles with my X-Server.  Prior to my mishap I had gone in to xorg and attempted to manually change the refresh rate of my monitor.  On a restart of x this then caused a communication error between my video card, x-server, and my monitor.  I went through and fixed it with Vesa on the command prompt.  The problem is, is that I'm now looking at a screen resolution of 1024 x 768 where I want a 1280 x 1024.  

Not only that but a few other settings I looked at in xorg are not what they used to be.  I added 1280 x 1024 into the xorg file and restarted X again but there is no option for that in my resolution settings.

Is there a way to get xorg to pick up on all my settings like I had before the change?  I know there is a backup somewhere, it should have auto created one when I opened xorg the first time.

---

### Post by moore.bryan on 2007-03-14
[I]i am correcting in assuming you did a "xserver-xorg reconfigure?"

were you getting the correct res BEFORE the tinkering?
[/I]

---

### Post by siciliancasanova on 2007-03-14
Yes I was and found a thread after the fact that explained in better detail how to change the refresh rate.  So everything was pretty good before the tinkering, especially the resolution, that was how I wanted it.

---

### Post by moore.bryan on 2007-03-14
*and now it's all busted-up?  did you try another reconfig?*

---

### Post by siciliancasanova on 2007-03-14
Yeah it didn't do anything for me at all.  All it asked was for the screen resolution, which I gave it what I wanted but didn't change again after a save and a restart.

---

### Post by moore.bryan on 2007-03-14
[I]there's a post around here somewhere talking about how to manually set the mode of your specific monitor and there's some command to help you find it, but to hell if i can find it now that i need it!

try searching for these terms: "screen," "resolution," and "mode;" maybe you'll be luckier than i.
[/I]

---

### Post by siciliancasanova on 2007-03-14
Man I hate searching the forums sometime.  I'm not in the mood right now.  What sucks is that you search and you find someone with a problem so close to yours but not exactly the same, and myself I have only been using linux for a week so I have no clue how to take that information and modify it to my situation, yet.

---

### Post by alienexplorers on 2007-03-14
Did you try setting up a modeline in your xorg.conf file.  You can get a modeline program at: [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

You insert it in the monitor section of your xorg.conf file like below:

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    ModeLine       "1280x960_70.00" 120.8 1280 1368 1504 1728 960 961 964 999 -hsync +vsync
    Option         "DPMS"
EndSection

---

### Post by moore.bryan on 2007-03-14
> **alienexplorers said:**
> Did you try setting up a modeline in your xorg.conf file.  You can get a modeline program at: [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)
*that's the exact program i was thinking of!!!!  :-0*

---

### Post by siciliancasanova on 2007-03-14
Ok so this is what I have now through vesa:```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60 
EndSection

```

This is modeline:```
 # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
```


Would someone be willing to put this in for me?

---

### Post by alienexplorers on 2007-03-14
Just edit your xorg.conf with your favorite text editor and enter the line on a line under your vertrefresh line. Save the file and reboot.

---

### Post by siciliancasanova on 2007-03-14
Still not working, the changes are saved but it's obviously not applying them.

---

### Post by alienexplorers on 2007-03-14
Forgot to mention that you need to add 1280x1024 to your Screen section of xorg.conf:

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by siciliancasanova on 2007-03-14
I already did that before, still nothing.

---

### Post by siciliancasanova on 2007-03-14
Bump

If anyone out there knows what I need to do.

I saved my xorg file after trying to set the refresh rate and it the x-server wouldn't load.  I reconfigured the xorg file with Vesa but now am looking at a lower screen resolution that is still not configurable after modifying the xorg file with the intended resolution and refresh rate.

---

### Post by siciliancasanova on 2007-03-14
Bump

---

### Post by ljpm on 2007-03-14
> **siciliancasanova said:**
> Ok so this is what I have now through vesa:```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60 
EndSection

```

This is modeline:```
 # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
```


Would someone be willing to put this in for me?

Are those the proper HorizSync and VertRefresh values for your monitor?

If these values are not correct it can cause poor resolution.

---

### Post by siciliancasanova on 2007-03-14
HP vs17, I believe can run at 75Hz, on the search I did.  Unless it was faulty info.

EDIT:  I haven't worked with the HorizSync and VertRefresh on those lines before.  What do I need to change there?

---

### Post by ljpm on 2007-03-14
Look up the ranges for your monitor (google if you don't have the manual). Enter these values.

---

### Post by alienexplorers on 2007-03-15
HP VS17 Monitor
Horiz = 30-83
Vert = 50-76
Max Res = 1280x1024 (75hz Vert)

---

### Post by siciliancasanova on 2007-03-15
Thanks for the suggestions but I already did all of that.

---

### Post by wilberfan on 2007-03-18
> **alienexplorers said:**
> Did you try setting up a modeline in your xorg.conf file.  You can get a modeline program at: [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

You insert it in the monitor section of your xorg.conf file like below:

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    ModeLine       "1280x1024_60.00" 108.88 1280 1360 1496 1712   1024 1025 1028 1060  -HSync +Vsync
    Option         "DPMS"
EndSection

Just by way of reminding myself (!), this method got my new Feisty Herd 5 screen resolution to where I wanted it (1280x1024 @60).   :)      (don't forget this, too: [http://www.ubuntuforums.org/showpost.php?p=2298970&postcount=13](http://www.ubuntuforums.org/showpost.php?p=2298970&postcount=13)) 

(Not a good sign, though, that I had to do this *manually!*    I sure hope the official release next month works better than this at recognizing my hardware!)

---

