---
title: "thinkpad x40 w/ 1680x1050?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by fartonmyear on 2007-03-22
i know this topic has been beaten to death. but i can't for the life of me get my dell 2005fpw to work. when i plug it in and switch monitors i only get the resolution of my laptop 1024x768. can someone please guide me to the answer?

---

### Post by tipsqueal on 2007-03-22
What kind of gfx card does it have? If it has an Nvidia, try installing the beta drivers that helped me out when using 1680x1050, but that was on a PC not a laptop using a Viewsonic monitor. Also to help us help you could you tell us what you have tried so far, if anything?

---

### Post by martinw89 on 2007-03-22
I believe the x40 has an integrated 855GM.  Make sure of this before you do any of the following.

First, get the package ```
sudo apt-get install xserver-xorg-video-intel
```  

Then, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```That should allow the full range of resolutions.

-Martin

---

