---
title: "[SOLVED] KDE won't start up"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by tennisplaya05 on 2007-07-31
Well, I did some updating, as well as trying to install nvidia drivers, before rebooting. 
After doing so, Kubuntu would boot up, then get stuck with some bcm43xx_microcode5.fw problem. Which apparently is a wireless card problem; i seemed to have fixed this with fwcutter. As well as removing my wireless card itself (which i never use anyway) 

This however led to a new problem. Now when booting, kubuntu will load up, but at the brink when KDE should load, im getting a blank screen. Not the *blank* screen, but just a blank screen. I can type things in, just with no response. Luckily i have access to command line with ctrl+alt+F1. 
i noticed that the last thing the bootup process says is:

kinit: no resume image, doing normal boot.

only problem is its NOT booting. 
Im familiar with videocard driver problems, (getting the black screen, wrong virtual resolution rates, etc.) And this doesn't seem to be the same; even though i just installed a new nvidia driver, and those would be the exact problems i would expect. 

Any suggestions on what the problem might be?
cheers.

---

### Post by apswartz on 2007-08-01
Post your /etc/X11/xorg.conf file

and the comments of your /var/log/Xorg.0.log file

---

### Post by tennisplaya05 on 2007-08-02
actually, don't worry about it. I was thinking it was an error with KDE
Turns out there was a problem with the xserver starting up. 

All fixed now.

---

### Post by upthelum on 2007-08-02
You could mark the thread as "solved" as well.

---

### Post by TechieZero on 2007-08-22
> **tennisplaya05 said:**
> actually, don't worry about it. I was thinking it was an error with KDE
Turns out there was a problem with the xserver starting up. 

All fixed now.

HOW did you fix this? I had the same issue after doing the exact same thing (sans the wireless card) and basically just did a reinstall since I had just installed it. Now I am afraid of trying to update the stock install of the Nvidia driver for fear of this issue now that I have invested some time in the current install.

---

