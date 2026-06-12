---
title: "Nvidia 7900 GS"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Marauderllc on 2007-05-17
Alright, I've been beating my head over this one for a couple of days now.

I'm running ubuntu fiesty on my brand new system, and everything is great except I can't get the latest nvidia drivers running and have been stuck with the generic ones.  Every attempt to enable the nvidia drivers with any of the dozen or so work arounds I have found result in only being able to run in text mode, manually editing the xserver back to the generic stuff and rebooting.

So, I've searched and searched and tried and tried again and upon exhausting every reasonable option I ask to community for assistance in my quest to fully enable a very nice video card.  
Assistance is of course greatly appreciated and I hope to become knowledgeable enough to return the favor in spades to the community at large.

In case the details are needed here they are
Athlon 64 x2 5600+
xfx geforce 7900 gs
gigabyte M57 sli motherboard.

---

### Post by Hobo Joe on 2007-05-17
Have you tried [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

---

### Post by krisfrajer on 2007-05-17
hahaha I have try to install my radeon ATi... I have try in the last two YEARS and no success... oohh just Kiddind. Installing these cards seems to required quite a bit of experience. I have try to do it for ferw days and then I decide to take few days off before trying again. I will do my best this weekend and if I hit on the nail I let you know... you know to share the knowledge with the community. Hopefully I can get a PhD. of how to install video cards this weekend ;) (Gosh... sounds so GEEK)

By the way... we share AMD architecture... 
I will subscribe your thread to my list... so to have your thread handy this weekend.
Good luck!

---

### Post by Hobo Joe on 2007-05-17
> **krisfrajer said:**
> hahaha I have try to install my radeon ATi... I have try in the last two YEARS and no success... oohh just Kiddind. Installing these cards seems to required quite a bit of experience. I have try to do it for ferw days and then I decide to take few days off before trying again. I will do my best this weekend and if I hit on the nail I let you know... you know to share the knowledge with the community. Hopefully I can get a PhD. of how to install video cards this weekend ;) (Gosh... sounds so GEEK)

By the way... we share AMD architecture... 
I will subscribe your thread to my list... so to have your thread handy this weekend.
Good luck!

Well, installing ATi cards is a whole nother story.... I've had no luck with that, but with nVidia cards it's a breeze.
Sorry to rub it in. :)

---

### Post by krisfrajer on 2007-05-18
Thus thread might be helpful... try at your own risk!

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by Cappy on 2007-05-18
I have the same card and I helped someone install drivers for their 7900GS today.
[http://ubuntuforums.org/showthread.php?t=432056&page=4](http://ubuntuforums.org/showthread.php?t=432056&page=4)

Edit:
Just to let you know, I found out how to do that by reading this thread:
[http://ubuntuforums.org/showthread.php?t=443846&highlight=nvidia-kernel-common](http://ubuntuforums.org/showthread.php?t=443846&highlight=nvidia-kernel-common)
It has some additional information I didn't have to use.

---

### Post by Marauderllc on 2007-05-18
Thanks very much cappy.

I'm a lot closer but still not quite there.  Under restricted drivers manager it says the nvidia driver is in use, but when I run the system test in cedega it says failed.   

So i'm thinking the driver is installed but perhaps not in use, i've checked my xconfig and it says the driver type is nvidia, which would suggest my theory is wrong however.  Any ideas?

---

### Post by Marauderllc on 2007-05-18
Okay, I now feel like a total idiot.  I solved this issue while following instructions to get flash player working on 64 bit installs.  Seems cedega also relies upon the 32 bit compatibility packages.  

So advice for all who follow in my footsteps.
Do what cappy says, don't forget to install the 32 bit compatibility.  Your issues should now be solved and you can put away the giant jug of vodka.

---

### Post by psyopper on 2007-05-18
> **Cappy said:**
> 
Edit:
Just to let you know, I found out how to do that by reading this thread:
[http://ubuntuforums.org/showthread.php?t=443846&highlight=nvidia-kernel-common](http://ubuntuforums.org/showthread.php?t=443846&highlight=nvidia-kernel-common)
It has some additional information I didn't have to use.

Wow, I'm a total newbie and one of my threads got pimped!

Woohoo!

---

