---
title: "Feisty Fawn installation problem"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by kcee on 2007-05-04
I'm trying to install Feisty Fawn on my Acer 5110 laptop with AMDTurion 64x2 and a Broadcom wireless card.  I keep getting the error message Microcode "bcm43xx_microcode5.fw"not found or load failed, and I can't get past it.  I'd appreciate any suggestions - thanks for your help.

---

### Post by TheDogDidIt on 2007-05-04
have you looked at - 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

or 

[http://ubuntuforums.org/showthread.php?t=391961](http://ubuntuforums.org/showthread.php?t=391961)

---

### Post by teddybairs1 on 2007-05-04
Are you using the release .iso or the beta?

It looks for the firmware for bcm43xx but shouldn't stop after that. The only time it did that for me was on a beta cd.

---

### Post by kcee on 2007-05-05
Hi, 

  Thanks for the reply.  I'm using the iso that I downloaded from the main Ubuntu site a couple of days ago.

---

### Post by teddybairs1 on 2007-05-05
Just for experiment's sake, have you tried removing your wifi card and then installing Ubuntu? No, you shouldn't have to do that, I agree. But for some reason it's getting hung with the bcm43xx firmware issue. Did the card work under Windows? Probably a dumb question, but figured I'd ask.

In the process of elimination, we need to find out what's causing it to hang. So, if it's hanging on the wifi card for some reason, try removing it, and then installing. If it still can't load, it's not the card.

another thing to question is the cd itself. Maybe it's not the .iso but the physical cd you burned it on to. I've had trouble before because of a cheap cd-r not burning or retaining the information properly.

Try burning a fresh cd on a different cd-r, preferably a different brand than the one the first one was, and see if that doesn't change anything.

Also, are you getting this message from an attempted install, or from an attempted load to livecd?

---

