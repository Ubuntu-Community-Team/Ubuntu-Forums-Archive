---
title: "Can't boot ubuntu 6.10 from liveCD?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by SilverApple on 2006-11-08
Hi All, I've been an Ubuntu user for about 4 months now and recently I decided to upgrade to edgy and just do a fresh install. Unfortunately the live cd will not boot up in standard or in safe mode so I'm at a loss as to what to do. I'm positive that the problem involves by sapphire ATI Radeon X850XT PE card. In dapper I was able to simply boot the liveCD with safe graphics settings, but in Edgy even this will not work. I tried looking up this problem in the forums and google but all I found were people having problems getting the drivers and such to work, but I don't even know how to get the base system installed. If this has already been posted I apologize, I was just unable to find this specific problem

Thanks for the Help!](*,)

---

### Post by taurus on 2006-11-08
I think you should try to use the alternate CD to install it on your machine.  It uses text so no need to boot into LiveCD before you can install it...

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by underdog on 2006-11-08
have you tried different vga=xxx options at boot? I'm not sure what you would use, but this might help.

---

### Post by ifross on 2006-11-08
I had what seems to be the same problem, so I got the alternate CD ad did a command line system, then i did a sudo apt-get install ubuntu-desktop, it worked and now I have a lovely edgy system

---

### Post by mastercheif on 2006-11-08
Yea, I am having the same problem. I downloaded the Edgy Live CD AMD 64, and my X800XT AGP seems to be having problems with it. The new login screen won't even render correctly.

---

### Post by SilverApple on 2006-11-10
Hi all, Sorry I didn't get back to you sooner, I've been sick the past couple days. Thanks ahead of time for all the advice. I went ahead and tried to do a text mode install from the alternate install cd. Everything went just fine until I rebooted the system. The Ubuntu loading screen showed up and then all the colors went crazy and inverted themselves. After this there were two blue and green lines across my screen.  It appears that I am at the command line but rendering issues make it so that I can't read what I'm typing. I tried to enter some commands blindfolded such as "apt-get install ubuntu-desktop" then I restarted but I still get the same thing, don't really know what else to do from here, hope that one smarter than me does.:mrgreen: :twisted: ](*,)

---

### Post by taurus on 2006-11-10
Boot your machine into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by wavetheory on 2006-11-10
> **ifross said:**
> I had what seems to be the same problem, so I got the alternate CD ad did a command line system, then i did a sudo apt-get install ubuntu-desktop, it worked and now I have a lovely edgy system

I had the same problem -- but before I upgrade to Edgy I'd REALLY like to try it out using the desktop CD.  In 6.06 I was able to boot from the Desktop CD fine using safe graphics mode (but had problems otherwise, and once I permenently installed 6.06 had to tune up the *xorg.conf* file to get the performance I wanted. . .).  So anybody have any workarounds so I can testdrive Edgy from the Desktop CD?
thx much

---

