---
title: "Problem with intel drivers"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-22
Alright, here's my odd problem. I have an onboard intel chipset. No graphics card. I've tried two different intel drivers for my system. On Windows XP, I used **Intel(R) 82845G Graphics Controller** and everything worked completely fine. However, here are the two drivers I've tried on Ubuntu and my issues with each of them

(I don't know the names of the drivers, so I'll just tell you what command I used to install them)

**_sudo apt-get install xserver-xorg-video-i810_**
This driver is the one that seems to work with video games (World of Warcraft, Stepmania) flawlessly, however, it won't let me change to my preferred resolution (1152x864). I've tried reconfiguring it using "sudo dpkg-reconfigure xserver-xorg" to no avail. This works for everything but my preferred resolution.

**_sudo apt-get install xserver-xorg-video-intel_**
This one works with my preferred resolution after configuring it with "sudo dpkg-reconfigure xserver-xorg", wooot! 1152x864 @ 75hz baby! Only one problem: It doesn't play games. I've tried running World of Warcraft, and it said something about 3d acceleration not being enabled or not installed or something like that. I've tried running StepMania, and it made the screen black and just kept flickering.

Can somebody please help me? I have 2 drivers that work for 2 different things but I can't find one that works for both! =(

Thanks in advance!

---

### Post by jpeddicord on 2007-06-22
Hi,

All you need to install is the package **915resolution**.
```
sudo apt-get install 915resolution
```

Restart your system, and you should be able to use that custom resolution in no time. ;)
However, be aware that not all games support custom resolutions. I do know Stepmania (great game, I'm actually redownloading it now) does however.


Jacob

---

### Post by Exershio on 2007-06-22
I'll try that, thanks a lot. And no, I only like to run my desktop in that resolution. When playing stepmania, I prefer it in windowed mode at 1024x768. Same with World of Warcraft, and pretty much all games I play.

---

### Post by Exershio on 2007-06-22
Now that I have 915 resolution installed, what do I do to get my resolution at 1152x864 and my refresh rate at 75?

---

### Post by wapfu on 2007-06-22
Hi,
Given That i have the same intel controller, how do i get feisty to recognise it?
When i installed it applied the xorg thingee.
Would like to use the controller on the motherboard as the current ATI card is not recognised.
Thanks
Best regards
Bill

---

### Post by Exershio on 2007-06-23
I still can't get this to work. I don't know what to do with 915resolution. Can somebody help me? I'm not an experienced linux user.

---

### Post by brad1150 on 2008-05-03
I don't know how big of a bump this is, found this topic on a google search, but it seems related. I have the "Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)" adn I am trying to play stepmania. I did the check to see if it could do 3d rendering, and it said no. I looked in the xorg.conf and it said its using the "vesa" driver. How do I enable 3d rendering? I am also having sound card problems with stepmania.

---

### Post by goombah88 on 2008-05-03
> **brad1150 said:**
> I don't know how big of a bump this is, found this topic on a google search, but it seems related. I have the "Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)" adn I am trying to play stepmania. I did the check to see if it could do 3d rendering, and it said no. I looked in the xorg.conf and it said its using the "vesa" driver. How do I enable 3d rendering? I am also having sound card problems with stepmania.

for what it's worth brad1150, i have the same integrated intel graphics card and my xorg.conf says it's using the "i810" driver...so you could always try that i guess.

---

### Post by Unix_Slayer on 2008-05-03
This why I dumped the Intel video. Bypassed them with dual Nvidia cards.\\:D/

---

