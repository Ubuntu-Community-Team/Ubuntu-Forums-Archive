---
title: "Games on the PowerPC"
date: 2006-09-01
forum: Apple PPC Users
---

### Post by mikeym on 2006-09-01
Hi there,

I'm due to inherit shortly a PowerPC based Mac (well at least I think it is as I'm sure it's over a year old) and I was wondering what my hope of running games on it might be. 

I would idealy like to run Ubuntu on it as I like it as an OS. It looks like I wont be able to run games using Wine, are there any other options?

Would OSX fare any better?

I am talking about some of the recent-ish generation of games like Halflife 2, Doom 3, Quake 4.

---

### Post by tidris on 2006-09-01
I don't know if this will apply to your machine, but on my dual G5 with a Radeon 9800 Pro video card any attempt to run 3D software results in the machine locking up and have to cycle power to recover. This happens even with the 3D screen savers that come with Ubuntu.

You should also know that ATI doesn't release device drivers for PPC Linux, so don't expect great performance from any ATI card on a PPC machine running Linux. OSX doesn't have that problem.

---

### Post by 3rdalbum on 2006-09-02
OS X is your best bet for running games on it. The Linux open-source ATI driver is not good enough for gaming, and all the commercial games are compiled for x86.

---

### Post by mikeym on 2006-09-02
> **3rdalbum said:**
> OS X is your best bet for running games on it. The Linux open-source ATI driver is not good enough for gaming, and all the commercial games are compiled for x86.

Does that mean that there is no way to run commertial games on a non-intel mac?

Are there mac projects to port games accross to the mac?

How does the release of the mac bootcamp windows drivers effect linux? Will there be improoved drivers at some future time?

---

### Post by APU on 2006-09-02
You can ONLY run games that are available for PowerPC and yes that means almost no commercial games under Linux.

Wine won´t help either because it can´t emulate a x86 CPU on a PPC Mac and the same is true for Bootcamp. Both are just for x86 hardware!

If you want to play commercial games you better go with MacOS X. Ther aren´t as many games as there are for windows but definitely more than for x86 Linux.

---

### Post by mikeym on 2006-09-02
> **APU said:**
> 
If you want to play commercial games you better go with MacOS X. Ther aren´t as many games as there are for windows but definitely more than for x86 Linux.

Hold on, if I'm getting you right here, then you are saying that for the intel based CPU you are best of with OSX, but if it's an intel based CPU couldn't you just use linux and Wine to get all the windows games working? Even perhaps making use of the bootcamp drivers for the Mac cards etc. 

Unless you wernt meaning the intel CPUs when you said x86 and ment the PowerPC CPUs. :-?  

Anyway I'll wait and see what I end up with. I'll try out OSX and if it drives me up the wall I'll give Ubuntu a whirl on the Mac.

---

### Post by APU on 2006-09-02
OK it might have been a little bit unclear...

Neither Wine nor Bootcamp will help on a PPC Mac

If you want to play games on a PPC Mac you are better off using MacOS X

There are more commercial games for MacOS X/PPC than there are for Linux, even on the x86 platform.

Additionally: If you want to play games on a Intel Mac - use Windows and don´t care about how much this hurts the mac ;-)

---

### Post by stmiller on 2006-09-04
There are no PPC Linux 3D video card drivers from ATI or Nvidia. No 3D on the powermac. There is some 3D functionality with some radeon cards, but it's not 100%. Sorry, no gaming. :(  

Lots of good games for PPC OS X, if you look around. Quake 3 runs well.

---

### Post by jpowermacg5 on 2006-09-04
If you change your driver to radeon in xorg.conf, you'll get great performance playing Planet Tux Racer (or whatever the heck it's called now-a-days). It's pretty fun for a (mostly default 3D linux game)

You probably can get away with q3 engine based games on linux with ATI.. but that's probably about it.

Stick with OSX.... I got so many games for OSX now... no time to play them all.

---

