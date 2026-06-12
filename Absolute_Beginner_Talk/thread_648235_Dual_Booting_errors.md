---
title: "Dual Booting errors"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by ConnorMac on 2007-12-23
Hi there, I'm new to the Ubuntu community, but have tried Ubuntu out before on a friends computer. Which prompted me to try it out dual booting with WinXP. I followed the easy step by step directions for dual booting. I got to the screen where it asks quite a few questions, the first one being "Start or install Ubuntu". I clicked on it, it went through the motions...then it stopped.
The screen flickered 6 times in about a 90 second timeframe, then went to some error screen that said "The display blah blah blah, as it just tried 6 times in 90 seconds. There might be an issue. Ubuntu will try again in 2 minutes. " ,then it had some error code that i didnt understand too well. During the screen flickers I saw colored lines each time at the top. Here are some of my system specs. Hopefully someone can help me.

Pentium 4 (T2250 @ 1.73ghz)
2gb DDR2
Ati Mobility x1400 PCI Express
120gb HD

:confused::confused:

---

### Post by autocrosser on 2007-12-23
Try starting in "safe graphics mode" & see what happens.

---

### Post by bumanie on 2007-12-23
What type and model of graphics card do you have?

---

### Post by ConnorMac on 2007-12-23
I have an ATI Radeon Mobility x1400 PCI-Express video card.

Also, how do I get to boot in safe graphics mode?.:confused:..

---

### Post by Moop on 2007-12-23
Have you checked the cd for errors? It might just be a problem with the install cd.

 You could also try using the alternate install cd which seems to work well for people with display problems.

---

### Post by bumanie on 2007-12-23
I have not installed an ati card personally, but did you try to install the driver from this site?
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
However, as you can't get into your system I think this would be not helpful at this point in time. When I installed a nvidia into gutsy I had the same behaviour occur.
What I had to do was press CTRL-ALT-F1 to get into a console and then turn off x server, install the video card driver whilst x-server was off and then turn x-server back on.
I can't tell you whether the procedure is the same for ati. 
I actually reinstalled at this point (when the monitor switched on/off every few seconds) and made sure I installed the driver from the nvidia site and all went well. You may need to reinstall and follow this guide (or something similar)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Sorry i can't be of more help, but as I said I don't have an ati card, so I have no real experience with them.

---

