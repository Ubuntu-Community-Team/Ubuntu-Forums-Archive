---
title: "[SOLVED] Setting graphics parameters"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-02-16
I bought a new LCD monitor. (Acer 2223WD) and it won't work with my Ubuntu system.

As near as I can tell, the problem is the monitor only accepts a 60Hz refresh rate and the drivers for my old ATI Radeon 9200SE graphics card will not let me reset it from the 86Hz (according to the "Screen Resolution Preferences" utility.) default. (Which is nice on my old CRT: No noticeable flicker.) I guess a fast refresh rate isn't needed with an LCD, since LCDs don't have the rapidly fading phosphors of a CRT.

The device manager shows the device as "RV280 [Radeon 9200 SE]".

If this isn't fixable, any recommendations for a new graphics card that doesn't cost an arm and a leg?

I generally don't go with high end graphics cards 'cause I'm not a gamer. . . Though I do go with pretty good processors & c. 'cause I do the "Digital Audio Workstation" thing.

Thanks in advance.

---

### Post by Quintin Riis on 2007-02-16
dpkg-reconfigure xserver-xorg maybe?  What drivers are you using?

---

### Post by jrlii on 2007-02-17
I'm trying that. The autodetect couldn't find any drivers for the ATI Radeon 9200 SE

---

### Post by jrlii on 2007-02-17
That got it! 

It took a couple of iterations: once with the CRT to get a 60Hz refresh rate and again after hooking up the new monitor and doing an auto detect on the monitor.

Thanks!

---

### Post by Quintin Riis on 2007-02-17
If auto-detection of the card fails, you can always specify manually what to use.  In your case either fglrx or ati.  

You're welcome.  Glad I could help.

---

