---
title: "Psychedelic Screen! (G3 Pismo/Ubuntu 10.04.4 LTS)"
date: 2012-03-19
forum: Apple Hardware Users
---

### Post by justinrockercts on 2012-03-19
Hello!

Recently I installed Ubuntu 10.04.4 LTS (Lucid) on my Powerbook G3 Pismo(net boot). I have been through hell and back for the past couple weeks trying to install Ubuntu on the computer and I finally have! HOWEVER...the display is all out of wack. I have edited the xorg.conf many many times, but I still have the same exact problem...

Once Ubuntu boots, I get a "LOW GRAPHICS MODE" message except it is highlighted in a bright red and looks funky.

Then once it boots I get a rainbow screen of death(The colors are all off, the wallpaper is a "rainbow swirl"). The OS is running fine, and it all works, except the displays colors. Now if the solution is to edit the xorg.conf, could someone be willing to give me in-depth instructions? Because i have edited it many many times only to find slight changes in the colors in the rainbow swirl, and real no solution. I am running extremely desperate after weeks of trying to do it myself(I'm not much of a techie) and really need help.

I have read thousands of posts(including this forum) and hours of research, and yet...nothing :(

Thanks all!

(I can email photos of what the screen looks like if needed)

---

### Post by rsavage on 2012-03-19
> **justinrockercts said:**
> 
I have read thousands of posts(including this forum) and hours of research, and yet...nothing :(


Have you looked at [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics) ?

---

### Post by justinrockercts on 2012-03-20
Thanks! That helped point me in the right direction but I am still out of luck. The computer uses a r128 - ATI Rage 128 video driver card, and many posts online are basically telling me I am screwed. There must be a way...

---

### Post by rsavage on 2012-03-20
The r128 can be difficult indeed, but not impossible.  Can you post the xorg.conf you have and the Xorg.0.log file?

---

### Post by justinrockercts on 2012-03-20
Here is my xorg.conf

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "true"
Option "NoInt10" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 30-80
VertRefresh 75-117
# 1024x768 74.90 Hz (CVT 0.79M3) hsync: 60.29 kHz; pclk: 82.00 MHz
Modeline "1024x768_75.00" 82.00 1024 1088 1192 1360 768 771 775 805 -hsync +vsy$
# 800x600 94.77 Hz (CVT) hsync: 60.37 kHz; pclk: 63.75 MHz
Modeline "800x600_95.00" 63.75 800 848 928 1056 600 603 607 637 -hsync +vsync
# 640x480 116.33 Hz (CVT) hsync: 60.14 kHz; pclk: 51.00 MHz
Modeline "640x480_117.00" 51.00 640 680 744 848 480 483 487 517 -hsync +vsync
Option "PreferredMode" "800x600_95.00"

Tthe Xorg.0.log file didnt show up....whats the best way to locate it? (im most likely making the tiniest mistake....

thanks for all your help thus far....i hope that helps

---

### Post by rsavage on 2012-03-20
Well if I was to hazard a guess I would say that monitor section is not from a pismo.
 
I would recommend you start a fresh and follow the guide I linked. You need to look at the Xorg.0.log to find out what is happening and what alterations to make. It is in the diectory /var/log . 
 
If you really have to use somebody else's then this [http://mac.linux.be/content/xorgconf-file-pismo-karmic-koalalucid-lynx](http://mac.linux.be/content/xorgconf-file-pismo-karmic-koalalucid-lynx) may help. Remember, just because somebody has posted an xorg.conf file doesn't mean they know what they are doing.

---

### Post by justinrockercts on 2012-03-20
Okay, will do. As soon as I get home, I'll try and post the xorg.0.log. it's just dIfficult to see anything with the display so distorted. In regards to the xorg.conf, I have deleted the one I showed you multiple times  and pasted the one you just gave me a link to multiple times in the past, and it hasn't done anything. I've pasted it, saved it (control + x), then restart the computer, and it's always the same. Maybe im not saving properly? In response to the monitor, it definetly is a pismo, I must've screwed something up. 

I'll keep trying. I'll get that xorg.0.log on soon.

---

