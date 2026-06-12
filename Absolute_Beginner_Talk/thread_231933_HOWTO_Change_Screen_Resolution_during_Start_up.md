---
title: "HOWTO: Change Screen Resolution during Start up"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by textguru on 2006-08-08
Hi!

I have newly installed Ubuntu Linux on my PC and just notice that my video cannot handle screen resolution, on startup I just saw black screen and I cant do anything so I just power off the PC. Is it possible that I may change the resolution? Hope you might help.

---

### Post by Tomosaur on 2006-08-08
Ok, try this. You'll have to print this page out or write the instructions down.

When you're booting up, select the 'Recovery Mode' option.

Once everything is loaded, you'll be presented with white text on a black background. This is the terminal. You can login here like you would normally (ie, type your username, then your password).

Once you've logged in, type the following command:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BK
```
This will create a backup file of xorg.conf in case anything should go wrong later.

Next, try the following command:
```
sudo nano /etc/X11/xorg.conf
```

Nano is a text editor which you can use in the terminal. Scroll to the bottom of the file you just opened. You should be able to see a list of different colour depths and resolutions, they should look something like this:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "RM170"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```
The line which says 'depth' is the colour depth, the modes are the available resolutions. There is a line which says 'DefaultDepth'. Look for it, and decide whether this is too high for your vid card. If it is, change it to a lower depth (but only one that is listed in the file you're looking at). Then, remove the **resolutions** that you know you cannot handle. So, say for example you wanted colour depth 24, but could only handle 800x600, you would edit the line so it looked like this:

```

    SubSection     "Display"
        Depth       24
        Modes      "800x600" "720x400" "640x480"
    EndSubSection

```

Once you're happy, press Ctrl+O to save the file (you will be asked to type the name you want to save it as, just leave it at what it already is and press enter). Once saved, press Ctrl+X to exit.

You should now restart your machine and see if the changes have worked.

---

### Post by textguru on 2006-08-08
Thanks for the reply. I appreciate it. What I did is I do the following:

from [http://www.ubuntuforums.org/showthread.php?t=227944&highlight=resolution](http://www.ubuntuforums.org/showthread.php?t=227944&highlight=resolution)

boot to recovery mode
type dpkg-reconfigure xserver-xorg

:KS

---

