---
title: "Viewsonic GS771 monitor and ubuntu"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by kenyonswim on 2007-09-11
I have a viewsonic GS771 17" monitor that will only set at 640x480 @85 hz which is maddening.

I checked the viewsonic specifications at found the following resolutions could be used:
1280x1024 @ 66 hz
1152x870 @ 77 hz
1024X768@87 hz
800x600@110hz
640x480@135 hz

Horizontal freq is 30-70 and vertical is 50-180

Computer is a Netvista using the onboard Intel graphics card

Here is part of the xorg.conf file:
```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"

```

I tried manually changing everything, did the simple, medium and advanced reconfigures of each and xserver crashes everytime.

Can anyone provide any advice?

Thanks in advance.

---

### Post by SOULRiDER on 2007-09-11
I suggets you reconfigure it
```
sudo dpkg-reconfigure xserver-xorg
```
Good luck and post here if you run into any trouble.

---

### Post by autocrosser on 2007-09-12
Well--Looking at your xorg, do you have a:

SubSection "Display"
                    Depth     24
                    Modes "1024x768" "800x600" "640x480" ????

If you do, Please give a copy of your Xorg log in System Logs.

---

### Post by kenyonswim on 2007-09-12
@SOULRiDER

I had actually attempted that command, to no avail. 

@autocrosser

I was having problems just getting to view the xorg.conf file by itself.  

However, I was able to resolve the problem!

In the bios, I switched the video memory to 8 mb, and voila!  Glorious 1024x768 resolution!

Thanks for the help!  I'm sure I'll be back!

---

