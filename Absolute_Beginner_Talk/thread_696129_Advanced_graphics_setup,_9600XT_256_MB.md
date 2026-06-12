---
title: "Advanced graphics setup, 9600XT 256 MB"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Maxwell314 on 2008-02-13
Alright I am going to go out and grab a gig of ram to get my second computer up and running for a project computer. I played with it earlier with no success of getting any of the cool desktop features (graphic wise) and I tried following a few things i could dig up on google, but nothing seemed to even let me close to it. My system will be as follows:

ASUS A7N8X Deluxe
AMD Athlon XP 3200+ Barton (2.17 GHz)
Sapphire ATI Radeon 9600XT 256 MB - or - ATI Genuine Radeon 9800 128 MB; Both running AGP 8X
1 GB PC3200 DDR400 ram (2x512mb, dual channel mode)
Enermax 431W PSU
300 GB ATA/100 Seagate Barracuda 7200.8 RPM 8 MB Cache

I am fairly new to Linux (i have played with the Active CD derivatives, I am planning to format and install this OS onto the Hard Disk. I usually pick up on how to really get around inside operating systems fairly quickly but I might need you to take some baby steps if we start using some command lines and stuff. The configuration I tried before was not exactly the same (diff. cpu (P4), mobo, psu, and ram) but i have a feeling it's largely related to the graphics cards(same). Any response and help would be greatly appreciated.. Thank you.


EDIT: Oh yeah forgot to say, I want to configure it to run Beryl, because that seems just cool. Any other problems i might run into would be appreciated also.

---

### Post by Blutack on 2008-02-13
How long ago did you install the first time?
Since then Ubuntu has gained automatic driver install, so on first boot you should get a message about restricted drivers, enable it and have another go.
You could just use compiz-fusion as preinstalled, it probably has enough shiny stuff and flame effects to keep you happy.  Just install
compizconfig-settings-manager - Compiz configuration settings manager
to allow complete control over plugins/effects etc.  Good luck!
Be aware, your graphics card may still not support compiz by default so more tweaking may be required - get it installed, give it a try and get back to us...

---

### Post by Maxwell314 on 2008-02-13
Thanks for the response. I am going to install it tonight hopefully. All I've been able to find is the CD install, I'd prefer a DVD install if it includes more features (like knoppix does with CD/DVD) anyways going to do a quick search for the DVD install then I'll rebuild the computer and be in business

---

### Post by Maxwell314 on 2008-02-14
got compiz working, only problem i have now is that i cannot get more than 2 desktops for the cube... I am working on that.. I had to manually install the fglrt or whatever drivers and install xgl-server or whatever.. i think xgl was the answer though. Anyways it's working great now thats what matters, now for configuration.

---

