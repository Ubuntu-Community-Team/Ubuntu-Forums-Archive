---
title: "Installing ATI drivers on Dapper PowerPC"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by jburtonrider on 2006-11-12
Is there any way I can get an ATI driver for dapper on a powerpc? I want to run beryl and I cannot seem to find anything online that has helped. Someone please guide me through it. Thanks.

p.s. - I have an ATI Radeo 9600 on this powerbook G4.

---

### Post by AlphaMack on 2006-11-13
Sorry.  We're second class citizens here.  ATI only has i386 drivers.  You can complain appropriately to them, but they'll get around to it about the same time Duke Nukem Forever gets released.

---

### Post by jburtonrider on 2006-11-13
Then honestly, can you do anything with ubuntu and a powerpc because I'm sick of dealing with all these compatibility issues. I might as well just stick with Mac OSX and forget about linux for now.

---

### Post by stream303 on 2006-11-13
I think the Feisty Fawn is supposed to have a lot of support for Beryl - I could be wrong.  

Until then, I'm just doing 2D stuff with the open-source driver, editing/printing wedding photos in the Gimp while listening to various internet radio streams...

---

### Post by stmiller on 2006-11-13
Yep- ATI does not make PPC Linux drivers. :(
In fact, their x86 Linux drivers are very poor, and not under great development at all.

I have a powermac G5 with an ATI Radeon card, but cannot play tux racer. Or anything 3D.
 

Nvidia has the best video drivers, for x86 Linux. (not ppc).

---

### Post by kellogs on 2006-11-14
you can make the free driver work by putting :

Option "UseFBDev" "false"

in xorg.conf in the device section.

warning: It does HANG, sometime lately, sometimes it take hours, I tested it with all kind of options, no luck.

Until devs at xorg or ubuntu find a way to this, we will have to wait to have 3d aceleration in ubuntu ppc, if we have it at all in the near future.

I dont see it clear though, now that ubuntu is considering ditching ppc :-| in next ubuntu release.

---

### Post by ssam on 2006-11-14
the older ati cards are supported quite well out of the box with the open source radeon driver. i think the 9600 is an r300 series which is now supported ([http://en.wikipedia.org/wiki/Radeon)](http://en.wikipedia.org/wiki/Radeon)).

i have used compiz on a 9000 mobility.

aiglx is enabled by default in edgy if your graphics card can manage it. there is the [blue compiz bug]("https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373"), but you can down load a fixed version of xorg (from that bug report)

---

