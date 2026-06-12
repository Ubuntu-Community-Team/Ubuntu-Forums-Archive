---
title: "EasyUbuntu: just some basic questions"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by chocomoojuice on 2006-12-11
First thing I want to say (not regarding this topic), I managed to make a dual boot installation of Ubuntu and XP, and it's wonderful.  And it's all thanks to the terrific HOWTOs, tips and tricks found on this forum.  Thanks Ubuntu forums =D!

Onto the questions...

1)  What is the current version of Easy Ubuntu?  Based on a sticky I found in the Faq section of the forum, it is Easy Ubuntu 2.4 beta, found at [this link]("http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta").  However, I also searched the web and came up with [ this rather official looking website]("http://easyubuntu.freecontrib.org/get.html"), which claims the current version for the Edgy distro is the alpha release.  Now, I'm relatively sure alpha comes before beta, making the beta site the newest version, but the fact that the alpha location has an official look is getting me worried.

2)  Can I trust Easy Ubuntu to properly and automatically install a driver for my ATI Radeon 9250 (256mb) graphics card?  I already tried installing via tutorials, but in the end had Cedega repeatidly fail on graphics tests.  Is the driver installation truely automatic, as in I won't have to modify anything using the console?

---

### Post by Drakkor on 2006-12-11
I would just install Automatix2, it has more depth and programs that you can easily install/uninstall.

---

### Post by gh0st on 2006-12-11
I found this tutorial on how to use Automatix2 the other day. Might be of use to you.

[http://www.howtoforge.com/automatix_ubuntu](http://www.howtoforge.com/automatix_ubuntu)

It's pretty comprehensive

Dan

---

### Post by thepaul on 2006-12-11
Hi

I've installed easy ubuntu 3.022 release.  It works for my machine, Dell Inspiron 1000 and my Ubuntu 6.06.  I installed the alpha version first and it didn't work.

I notice there is a button to click for nvidia drivers, so it should work, I assume.  I'm not sure though.  No doubt others can help you.

take care

---

### Post by chocomoojuice on 2006-12-11
> I would just install Automatix2, it has more depth and programs that you can easily install/uninstall.

However, it does not provide the automatic install of the ATI driver, which I  desperately want if it's truly automatic.  I have automatix installed, and it is a fantastic program in its own respect.

---

### Post by marx2k on 2006-12-11
> **chocomoojuice said:**
> First thing I want to say (not regarding this topic), I managed to make a dual boot installation of Ubuntu and XP, and it's wonderful.  And it's all thanks to the terrific HOWTOs, tips and tricks found on this forum.  Thanks Ubuntu forums =D!


In reference to your dual booting, I also used to dual boot on 3 separate linux boxes, but since installing VMWare Server and installing XP as a virtual machine, I find I no longer need to have a dual boot of XP. At this point, I can't think of any reason that I would need a separate XP partition on my drive, taking up space. VMWare+XP Install is the perfect thing.

I would say you would only need a separate XP install if you want to play some serious 3D games only made for XP, but since thats why I have an XBox, PS2, Dreamcast, etc.. there's no need and I never have to bring down beloved Ubuntu in order to interact with XP.

---

### Post by chocomoojuice on 2006-12-11
> I would say you would only need a separate XP install if you want to play some serious 3D games only made for XP...

Actually, that's precisely my predicament.  I love to play Counter-Strike: Source, in conjunction with Ventrilo and Xfire, all of which are made specifically for Windows.

---

### Post by chocomoojuice on 2006-12-11
I can see a "ATI binary X.Org driver" available in Add/Remove Applications that supports my card model.  However, if I install it through this, am I having to go through all the console hub-bub?

---

### Post by igknighted on 2006-12-11
ATI drivers are usually pretty simple... try this if you haven't, it's always worked for me:

```
sudo aptitude update
```
```
sudo aptitude install xorg-drivers-fglrx
```
```
sudo aticonfig --initial
```

then ctrl-alt-backspc to restart X, and you should be good.  Open a terminal and type:
```
glxinfo | grep render
```
and if it says that direct rendering is enabled you should be all set.

---

