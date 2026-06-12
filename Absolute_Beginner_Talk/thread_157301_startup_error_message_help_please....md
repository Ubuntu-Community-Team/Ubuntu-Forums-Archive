---
title: "startup error message help please..."
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by xxFelixDCatxx on 2006-04-08
Okay so I've installed and everything and as I go to boot my laptop up, it now reads that there's a problem with the 'xserver'.  I'm relatively new to linux, but after reading into the error message details a bit, I believe this is a graphics application.

Does anyone know what I'm talking about/have any advice?

-linux n00b

---

### Post by dermotti on 2006-04-08
backup your /etc/X11/xorg.conf file

and run

**sudo dpkg-reconfigure xserver-xorg**

and select **vesa** as your video driver.

Hopefully this resolves it. if not, post the erros in here please.

**EDIT: Before you do the above, is your Xwindows starting properly? if so disregard above!**

---

### Post by xxFelixDCatxx on 2006-04-08
okay i ran the reconfigure and input everything, and i'm still getting a fail, it blue screens on me and puts out an error log, the following is the output

MergedFB does not work with option UseFBDev, Merged FB mode is disabled

and there are 3 no symbols found errors

I use a radeon x200 card built into my laptop, it auto-detects the card and everything about it, it also works with other distros, I can't find out why not with ubuntu.

---

