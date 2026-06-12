---
title: "Serious problems"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by bidget on 2008-04-03
So, first of all, my USB keyboard isn't detected in the grub menu, so I had to plug in an old ps2 keyboard, which worked fine. Now, that's not THAT big of a problem, but I'm sure in the near future my dad will want his keyboard back so I'm hoping there's a fix for it haha. Ok and now secondly, I installed Ubuntu, got through the installation fine, got into Ubuntu, installed all the updates... After restarting the computer, this is the screen I get. I'm thinking it's a problem with the graphics driver, but then again I'm not an expert.

**EDIT**

I was also forced to do a hard shutdown to restart the computer because I couldn't see anything, so I hope that didn't wreck anything :(

---

### Post by privaterolf on 2008-04-03
That's not necessarily a problem with the graphics card, just the configuration of the graphics card to the monitor.

I solved that by re-installing, but I'm sure there's another way.

Can you get it to start up in safe graphics mode?

---

### Post by PmDematagoda on 2008-04-03
Do you get this screen when starting up the PC and reaching GRUB or only when starting up Ubuntu?

---

### Post by bidget on 2008-04-03
This is the login screen where I type in my username and password (I think). I've already gotten through the grub menu. I'm going to give safe graphics mode a shot though. Hopefully that will do something

---

### Post by privaterolf on 2008-04-03
> **bidget said:**
> This is the login screen where I type in my username and password (I think). I've already gotten through the grub menu. I'm going to give safe graphics mode a shot though. Hopefully that will do something

Could you post your graphics card and monitor model for me, please?

---

### Post by bidget on 2008-04-03
So maybe I'm missing something but I don't see a safe graphics option... Theres the regular kernel, the recovery kernel, memtest86+, and my windows installation. My monitor is a Viewsonic G90f, and my video card is an eVGA GeForce 8800GT. I think I might have screwed it up though, when I was selecting what type of monitor I had I said it was a G90f+ because G90f wasn't in the list... But I made sure that it was still using a proper resolution and refresh rate, so I don't really know if that's what did it.

---

### Post by PmDematagoda on 2008-04-04
Boot Ubuntu in Recovery Mode, once Ubuntu boots up, execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
that will restore the default configurations for the X-Server, after that is done start the X-Server with:-
```
startx
```
Then see if that solves your problem to a certain degree.

---

### Post by bidget on 2008-04-04
Alright I reinstalled Ubuntu, seems to be working ok now (which it should be hahaha) I've installed the drivers for my 8800GT and I'm just installing the updates. The screen I attached above only appeared when I rebooted after installing the updates, so hopefully it shouldn't happen again :)

**EDIT**

Looks like we posted at the same time there PmDemetagoda hahaha :D. Hopefully it won't screw up again but if it does I will know what to try :)

---

