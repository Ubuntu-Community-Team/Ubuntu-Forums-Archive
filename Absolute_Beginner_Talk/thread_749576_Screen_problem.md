---
title: "Screen problem"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Guzman on 2008-04-08
Hi,

I just messed up my screen...
Was trying to change the type of monitor and choosed a LG but the wrong model, and then choose 1280X1024.

The thing is that now I cant see anything and I was hopping for some kind of voodoo to restore the old settings. All I want is the 1280X1024 but the default settings only give me 1024X768.

Thanks in advance,
Guz

---

### Post by Six_Digits on 2008-04-08
What kind of video card do you have?

[Read this]("http://ubuntuforums.org/showthread.php?t=690760&highlight=reconfigure+xserver") and see if you can find anything helpful.
The guide will bring you through a series of steps to configure your video card and monitor. One step also includes your choice of screen resolutions.

---

### Post by Guzman on 2008-04-09
I have a NVIDEA 6600 LE but Im running Ubuntu through  virtual box.

Im trying Ubuntu with virtual box just like in a teste drive, as im going to get familiarized with this OS. 

The goal is to get rid of XP at home in a close future and stick with Ubuntu, but for now I must run it using virtual box. Should I do a Dual boot? 

Thanks,
Guz

---

### Post by Tomatz on 2008-04-09
Use wubi instead of a virtual installation. It allows you to install ubuntu under windows (without partitioning etc)

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Crafty Kisses on 2008-04-09
> The thing is that now I cant see anything
By that do you mean, it's at a black screen?

---

### Post by Rocket2DMn on 2008-04-09
The link that Six_Digits gave you ( my own tutorial, hehe - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) ) should work for you with Virtual Box.  If selecting the "nv" driver doesn't work for you, you might need to use the fallback "vesa" driver.  You could try installing the restricted drivers for your Nvidia card, but I'm not sure how those will act under a VM.

Wubi is not an officially supported method, but some people seem to like it.  If you can't get your current setup to work, I would suggest doing a dual boot, there are plenty of HowTos for that, including [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
It's not very complicated, you basically just have to defrag your windows drive, then go to install and give Ubuntu as much space as you see fit.

---

### Post by Guzman on 2008-04-09
Nope, not black, just ultra-distorted and out of range.

---

