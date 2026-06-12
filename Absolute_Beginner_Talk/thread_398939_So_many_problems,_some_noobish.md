---
title: "So many problems, some noobish"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-04-01
Within the last 2 weeks I got a new video card.  An ATI 9550 i believe.  I have been using my machine to Dual boot with Xp and ubuntu.  When I added the new video card and attempted to boot ubuntu Server X failed to load and I was left at a command prompt.  

Now i have very little experience with doing things via a command line in linux.  When I installed ubuntu I went with the typical install options, and my account was not a root account.  (That makes senese to some of you guys right?)  Although I do have a password set for that.  

My question is what is the best way to get ubuntu to recognize my video card?  I know that their website offers linux drivers for my video card.  Should I just reinstall ubuntu and have it automatically configure to this new video card or is there some other way.  

Very lost right now.

---

### Post by Maestro23 on 2007-04-01
This guide should help you: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

or you can try and Envy script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck.

---

### Post by dstew on 2007-04-01
Probably the easiest way to get an ATI card to work is to install and use Envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by dracomordag on 2007-04-01
> **dreadh3ad said:**
> Within the last 2 weeks I got a new video card.  An ATI 9550 i believe.  I have been using my machine to Dual boot with Xp and ubuntu.  When I added the new video card and attempted to boot ubuntu Server X failed to load and I was left at a command prompt.  

Now i have very little experience with doing things via a command line in linux.  When I installed ubuntu I went with the typical install options, and my account was not a root account.  (That makes senese to some of you guys right?)  Although I do have a password set for that.  

My question is what is the best way to get ubuntu to recognize my video card?  I know that their website offers linux drivers for my video card.  Should I just reinstall ubuntu and have it automatically configure to this new video card or is there some other way.  

Very lost right now.
get to a command line (alt+F2), sudo dpkg-reconfigure xserver-xorg
choose the driver labeled ATI, hit enter or OK through everything else
then when you're back at the commandline, type startx

---

### Post by dreadh3ad on 2007-04-02
Thank you guys for everything :)

---

