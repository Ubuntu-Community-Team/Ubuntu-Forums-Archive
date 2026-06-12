---
title: "Color problem, G5 PPC, Nvidia, Ubuntu 9.10 Desktop"
date: 2010-01-11
forum: Apple Hardware Users
---

### Post by ripeart on 2010-01-11
Hello,

I'm having an issue with a new install of Ubuntu 9.10 Desktop on a G5 PPC Tower with an NVidia Mac G5 64MB GeForce FX5200 AGP Video Card. I've tested the configuration on two different video cards and get the same results.

For lack of a better term the colors are really wacked out.  It's almost as if the video signal was being put through a solarize filter in Photoshop. I took a screenshot and viewed it on another computer however it looks fine in the screenshot.

I've attempted to approximate the effect, below. Except the real image is about twice as bad, and almost unreadable.

[[IMG]http://img191.imageshack.us/img191/4062/screenshot1wl.th.png[/IMG]]("http://img191.imageshack.us/i/screenshot1wl.png/")

Any help or a point in the right direction would be great.

Thank you.

---

### Post by linuxopjemac on 2010-01-12
You can try this:
> Open totem movie player and navigate to edit -> preferences -> Display and click on Reset to defaults. No need to restart. This fixed the issue.
The problem is due to the wrong hue setting.

see [here]("http://ubuntuforums.org/showthread.php?t=1316151&highlight=hue")

Sorry, I didn't read well enouigh, I thought you had it with video playback...probably my fix does not work for you. The problem resides in a wrong Xorg.conf file.

---

### Post by linuxopjemac on 2010-01-12
take a look at this thread, you need to adapt teh Xorg.conf file to meet the needs of your particular video card:
[http://ubuntuforums.org/showthread.php?t=1139795](http://ubuntuforums.org/showthread.php?t=1139795)

Please report if the nouveau driver works for you.

---

### Post by ripeart on 2010-01-12
Thanks for getting back to me. So in the thread you posted there were two different solutions. One solution was to download and install the Nouveau drivers and associated files, then configure the xorg.conf file to force the use of such. I didn't have an xorg.conf file so I had to create one. I followed the thread advice however none of that worked.

The next fix was to customize the xorg.conf for my specific card. Thankfully my card was the same card mentioned so I was able to copy the working settings from the thread into my xorg.conf. However the machine then booted to a command line. I ran startx and the screen blinked several times and then threw a long error. One of the last errors I saw was something like: "Panic, no screens found."

I'm not at the mac right now however when I get back to it a bit later, what would you like me to post? My xorg.conf? Any error logs which might help?

I can't wait to get this working, Ubuntu runs incredibly fast on it! Thanks again for your help.

---

### Post by ripeart on 2010-01-12
OK! Got it working! Here's my xorg.conf file. It's the same as was posted in the other thread here: [http://ubuntuforums.org/showthread.php?t=1139795](http://ubuntuforums.org/showthread.php?t=1139795)

```
Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:240:16:0"
    Driver          "nouveau"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
        HorizSync      30-81
        VertRefresh    56-75
        Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1280x1024_60"
           EndSubSection
EndSection
```

How do I change the tag to RESOLVED?

---

### Post by linuxopjemac on 2010-01-13
I think you can edit the first post. I am not sure.

---

### Post by JBAlaska on 2010-01-13
Only problem with that solution is that the current "nouveau" driver has no 3D acceleration..
 Did you try using the proprietary NVIDIA graphics driver suggested in hardware drivers? They reportedly DO work with your GeForce FX5200 AGP

---

### Post by linuxopjemac on 2010-01-13
That will not work as these drivers don't exist for the PPC port.
[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

---

### Post by JBAlaska on 2010-01-13
Oh well...nouveau it is then.

Sorry

---

### Post by linuxopjemac on 2010-01-13
I don't know what the maximum resolution of your screen is, but you might want to tweak that as well.

---

