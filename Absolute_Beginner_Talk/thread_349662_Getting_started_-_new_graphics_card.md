---
title: "Getting started - new graphics card"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by richuu on 2007-01-30
Hi to all with my first post. Just got my first linux system up and running with Ubuntu 6.10, and can't be doing too bad, since I'm typing this on it.

However, after getting the basic system up, doing the updates etc., I added an AGP nVidia 5500fx and the system wouldn't boot. I get a BSOD equivalent, but in typical noob style, I didn't take the error message down. (Apologies to noobs with better fault finding techniques than me!) Should I install an nVidia driver before I put the new card in?

---

### Post by hardyn on 2007-01-30
X will be configured for your old card.

you will have to edit the xorg.conf file to match your new nvidia...  Im sure you could find such values on this forum somewhere... or.... reinstall if you are not too far into your last install.

---

### Post by igknighted on 2007-01-30
> **richuu said:**
> Hi to all with my first post. Just got my first linux system up and running with Ubuntu 6.10, and can't be doing too bad, since I'm typing this on it.

However, after getting the basic system up, doing the updates etc., I added an AGP nVidia 5500fx and the system wouldn't boot. I get a BSOD equivalent, but in typical noob style, I didn't take the error message down. (Apologies to noobs with better fault finding techniques than me!) Should I install an nVidia driver before I put the new card in?

Boot into recovery mode, then run this command:
```
dpkg-reconfigure xserver-xorg
```
youe will then be asked a series of questions, answer then the best you can and it will do the config for you.  When you are done, reboot and it should be fine.

---

