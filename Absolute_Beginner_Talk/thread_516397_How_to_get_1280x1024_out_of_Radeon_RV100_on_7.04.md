---
title: "How to get 1280x1024 out of Radeon RV100 on 7.04"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by itm on 2007-08-03
I've just installed Ubuntu 7.04 on an Athlon machine with Radeon RV100 graphics. The display adapter wasn't auto-detected, and I was initially only offered two screen resolutions: 800x600 and 640x480. I want to run at 1280x1024 at 60Hz, which is supported by my monitor.

Following some instructions that I found elsewhere I edited /etc/X11/xorg.conf and added 1280x1024 and 1024x768 to the "Screen" section. This expanded my range of available screen resolutions to include 1024x768, but 1280x1024 is still not available.

My next thought was that maybe I needed to manually install a driver for the RV100, but I can't find one anywhere. Can anyone advise me on how I can get 1280x1024 resolution out of this adapter?

The Monitor and screen sections from my /etc/X11/xorg.conf file are below:

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60 
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

EndSection

Section "Screen" 
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1 
        Modes        "1280x1024" "1024x768" "800x600" "640x480" 
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480" 
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display" 
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480" 
    EndSubSection
EndSection

---

### Post by startherepodcast on 2007-08-03
Hi,

Can you please post the details of your screen including 

[LIST]
[*]HorizSync 
[*]VertRefresh
[/LIST]

thanks

Adsized

---

### Post by ReaderRat on 2007-08-03
You might try:
```
sudo dpkg-reconfigure xserver-xorg
```
And put in the monitor Horizontal and Vertical refresh rates and choose the resolutions you want. 
Back up your /etc/X11/xorg.conf file first, so you can go back to it if this does not work.

[ATI Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by itm on 2007-08-03
Many thanks for the feedback - entering the refresh rates for my monitor into xorg.conf did the trick.

---

