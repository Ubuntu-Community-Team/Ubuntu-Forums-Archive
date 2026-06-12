---
title: "[SOLVED] Trying to fix screen resolution; editing xorg.conf?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by leialte on 2007-07-06
My monitor is capable of 1280x1024. I looked up my monitor model and it says the max refresh rate is 140Hz, my HF is 30-70 KHz and my VF is 50-160 Hz. 

Question 1: Should I go ahead and use these numbers to customize or play it safe and downplay those numbers?

I tried to find a solution to my problem without posting yet another resolution help thread, but I tried editing the xorg.conf -- managed to do something that forced me to reinstall, but that isn't my problem. I keep seeing these threads about the list of things you're supposed to see when you edit xorg.conf and I see absolutely nothing and I don't know what to do from here. I know it's impossible to be seeing nothing, so I'm probably not even seeing the file but I still don't know what to go about now.

I've tried sudo nano /etc/x11/xorg.conf, but I get a screen that says "GNU 2.0.2 File: /etc/x11/xorg/conf" at the top of the screen, and below a list of options like [new file] and ^G. I finally figured out the ^ means shift (how I destroyed the file the first time was trying to figure that out...)

I tried 'Get Help' but it didn't do me any good.

I also tried sudo dpkg-reconfigure -phigh xserver-xorg, even though I'm not entirely sure what that was supposed to accomplish. It seems to me it just backed up my xorg.conf file, which is fine by me.

Question 2: How do I use the backup file if I destroy the xorg.conf file again?

I also tried gksudo gedit /etc/x11/xorg.conf. It pops up gedit and shows me a blank file.

Question 3: What am I missing/What do I do now?

---

### Post by reckless2k2 on 2007-07-06
what kind of video card do you have? if you are using nvidia or ati, install their specific drivers first using the proprietary module. that might fix your problem without editing xorg. you'll have to reboot or restart X and then pick your new screen res from gui. if it's still not there, then edit xorg.

---

### Post by pigletx on 2007-07-06
I tried installing ubuntu yesterday and I have a similar experience, my monitor is capable of 1920x1080 yet ubuntu displays at 1024x768.

I know the fix is to edit xorg.conf it jus seems i shouldnt have to.
Why cant ubuntu give a long list of resolutions to try?? from 640x480 to 2500x1600 ...

On a side note it was nice that openchrome the drivers for my graphics was preinstalled :) I tried installing openchrome in opensuse once and it lead to x11 never loading up again. :/

---

### Post by Outrunner on 2007-07-06
> **leialte said:**
> 
Question 2: How do I use the backup file if I destroy the xorg.conf file again?

I also tried gksudo gedit /etc/x11/xorg.conf. It pops up gedit and shows me a blank file.

Question 3: What am I missing/What do I do now?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Notice the capital 'X' in X11... 

If you want to restore the file

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by leialte on 2007-07-06
Thank you Outrunner, the capitalization was my problem ^^;. I knew I had to be missing something...

Reckless: I have  an "nVidia Corporation NV18 [GeForce4 MX - nForce GPU]" (copied from below).

Question: proprietary module? EDIT: using Envy to install driver.

And related: before I had to reinstall, Ubuntu tried something with Nvidia (sorry, I saw Nvidia and clicked yes without really reading it *shoots self*) and it downloaded and installed something. When it was done I could only get 640x400 resolution, and 800x600 disappeared altogether. This automatic download request has not occurred again.

```

Section "Monitor"
        Identifier      "eView 17f3"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
        Monitor         "eView 17f3"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```

---

### Post by leialte on 2007-07-06
YIKES! I used Envy to install the driver and it did basically the same thing as the restricted driver manager -- now I can only use 640x480!!! HELP! Get me out of this thing!

```

    Device         "nVidia Corporation NV18 [GeForce4 MX - nForce GPU]"
    Monitor        "eView 17f3"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
   Monitor        "eView 17f3"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by deadlikeoscar on 2007-07-06
open a terminal and type nvidia-settings and see if you can select your desired resolution.

---

### Post by leialte on 2007-07-06
I tried that last time. The problem is the screen resolution is so small I can't see all of the Nvidia Settings window to do anything about it!

---

### Post by bsawler on 2007-07-06
x11 is case sensative. 

Please ensure you use **X**11/xorg.conf

---

### Post by bsawler on 2007-07-06
Sorry, about the last post. I only read the first post apparently. 

I had a similar card and I followed this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e)

---

### Post by Raineer on 2007-07-06
> 
I've tried sudo nano /etc/x11/xorg.conf, but I get a screen that says "GNU 2.0.2 File: /etc/x11/xorg/conf" at the top of the screen, and below a list of options like [new file] and ^G. I finally figured out the ^ means shift
Just so you know, ^G means "control-G", not shift

All you really need to know about nano is ^W is Write (Save), ^Q is Quit

You also didn't watch Case, as the directory is /etc/**X**11/xorg.conf

---

### Post by leialte on 2007-07-06
thank you bsawler, I'll try that link when I get home on break

raineer - I meant ctrl ^^; thnx

---

### Post by leialte on 2007-07-06
Woo hoo! I am officially in 1280x1024 resolution.

What I did: Envy messed up my computer and it did the whole 'can't find a monitor' bit.  I reconfigured my xorg.conf file, then I made sure I uninstalled nvidia glx (I think that's it) and nvidia-settings. Then I went into the xorg.conf file, added the horizsync and vertrefresh numbers as suggested by the website bsawler provided, and added 1280x1024 to the list of resolutions (it added 1024x768 automatically). The only thing was that the screen showed up distorted in the higher res, but a few settings in my monitor menu and it's as right as rain.

thanks everyone for your help!

---

