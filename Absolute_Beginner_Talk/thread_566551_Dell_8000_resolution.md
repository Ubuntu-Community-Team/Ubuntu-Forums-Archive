---
title: "Dell 8000 resolution"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by imagesbytjm on 2007-10-03
I am a complete newbe to linux (using Apples since 1983).  Loaded 6.06 on a Dell Insprion 8000 laptop just to see what linux was all about.  Worked through most of the issues with the help of the of online doc. and this fourm. These included fixing the horiz. sync and Vert refresh, getting the fans working, playing DVD's, making the WiFi card work and disabling of sleep (power management). 

Still one issue I can't seem to fix.  The 15" dell screen is capable of 1400x1050, but I 've been unable to get Ubuntu to allow that.  System--Preferences--Screen Resolution shows only the 1024x768, 800x600 and 640x480 no matter what I do. I've tried gediting the /etc/X11/xorg.conf to add the 1400x1050 but when I do I lose the 1024x768.  Tried adding 1400x1050 and eliminating 640x480 and still no go.  

I saw some posts about the 915resolution package, but I don't think that applies to this Dell. 

Dell PIII, 850Mhz, 256 Ram, ATI M4 Viedo.  With the changes to the Horiz sync and Vert. refresh the computer is showing a 85 Hz refresh rate.  I have the depth set to default=24.  

Any ideas?
Thanks

TJ

---

### Post by reckless2k2 on 2007-10-03
915 is related to intel if i'm not mistaken. have you tried to install the proprietary ati driver? even so, sometimes after you will have to edit xorg then it'll stick.

---

### Post by imagesbytjm on 2007-10-03
Yeah, if I am reading it right the 915resolution package is for intel graphics chips. I 've got the ATI M4.  I 've tried messing around with the /etc/X11/xorg.conf with several changes but nothing seems to work.  Seems like Ubuntu is stuck in those three standard resolutions that come with the download. 

TJ

---

### Post by imagesbytjm on 2007-10-03
OK, did some more searching on the forum and found the answer on my own. If anyone else is looking for it do search on dpkg-reconfigure xserver-xorg.

Now looking good at 1600x1200!  

I am starting to like this linux stuff. But not as much as may Mac's (sorry). 

TJ

---

