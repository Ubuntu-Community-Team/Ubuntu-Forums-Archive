---
title: "Porbably an old question but..."
date: 2007-08-25
forum: Apple PPC Users
---

### Post by falcon1620 on 2007-08-25
This question is probably old hat, but I cannot seem to find a solution that is working for me...I have worked on this for 4 hours already typing away and searching... I give up... Someone please help me. I have a G3 300Mhz, with a 3d Rage pro. Im trying to put Feisty Fawn (I think) its the latest off the mirror so far... on here. Every time I boot, the screen give me a frequency out of range error message... I tried live-powerpc video=ofonly and it boots, I can get into the console, but Xserver still fails to start, so you get frequency out of range. I went to the /etc/X11/xorg.conf file to take a look at it, and I see that the display is configured with the proper settings... all supported resolutions, it detects the apple display an fills in the correct frequency range for it..  30--85 and 47-160, and it also has the video driver picked out...however when x starts it launches into a video mode using 73.3 and 180 refresh rates. What the heck... It detects the ATI 3d Rage pro card, Id post my xorg.conf file but umm how do you do that with out a working GUI? I know what refresh rates its using because the apple display complains about it and shuts off... Please help this is very annoying!:confused: I would SSH into it also but again...

---

### Post by falcon1620 on 2007-08-25
by the way I just tried video=atyfb:vmode:6  and a few other options. The card keeps throwing the resolution into a 125Hz refresh rate, way outside of what any monitor can handle... This card doesn't listen to any Refresh rate values that I seem to type in also
video-atybf:1024x768@60 came up with 120Hz errr what is the deal with this thing...
:(:confused::mad:

---

### Post by stmiller on 2007-08-25
I think it may be this problem:

[https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70](https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70)

This is a fix. Let us know how it goes.

---

### Post by falcon1620 on 2007-08-26
Well I'm not familiar with apt-get so Ive strayed away from server, but I might try that, or the alternate install CD. I tried the above, but it is out of range, even on the console, so it only worked with the video=ofonly option. The only problem is that once you use that option, not much changes and I couldn't get anywhere with the configuration file (etc/X11/xorg.conf), so well try another method, but the live cd worked flawlessly with my other G3 that has a rage 128 on it... I'm very impressed that sound and the modem worked with it... A nice surprise. So I will give those other options a try and keep you all posted, maybe I can round up another rage pro 128 card for the mac, that might be an easy fix! I am going to use the problem child G3 for a server, since it has 3 100Gb drive for storage.  Rock solid Linux on PPC, I use some Power4's at work and Intel with Red Hat that is a rocken platform for stability. Got to love Linux... :) Thanks for your input...

---

