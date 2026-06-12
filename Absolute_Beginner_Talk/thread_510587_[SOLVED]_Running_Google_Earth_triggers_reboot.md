---
title: "[SOLVED] Running Google Earth triggers reboot"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-07-26
I installed Google Earth as instructed here: [http://ubuntuforums.org/showthread.php?t=233309&highlight=install+google+earth](http://ubuntuforums.org/showthread.php?t=233309&highlight=install+google+earth)

It appeared to be a successful install, but now every time I try to run the program, my system reboots. Any ideas?

---

### Post by skymera on 2007-07-26
mine runs fine.

however when i run HIGH graphics games in windows, like GarrysMod, it shuts down.
but if i lower the graphics it works.

i dont know if its the same boat your in.

maybe someone else can help more, :)

---

### Post by machavillain on 2007-07-26
Yeah, unfortunately that doesn't help me. Can anybody else lend a hand?

---

### Post by Paulmd on 2007-07-27
> **machavillain said:**
> Yeah, unfortunately that doesn't help me. Can anybody else lend a hand?

Need some info:

How much ram do you have?
What is the make and model of your video card (or chip), and how much RAM does IT have?

The main gist of this is: can Google Earth run on your config at all? 


Have you had any problems with OTHER 3d applications? if you do, it may be a problem with the video driver or hardware.

One thing I've seen on SOME old nVidia cards (riva/vanta era) is they have a nasty to overheat, and eventually stop working, but before they do, they crash a lot. The OTHER problem I've seen on old nVidia cards (newer generation than riva/vanta, but sill old) is that SOME of them have a problem with the capacitors, (they swell up and/or leak). If THAT's the case, then it's a bad video card.  [Also, if you have bad caps anywhere else, that's bad, and usually means replacing the part with the bad caps]


Run Memtest to check the ram, it's available during the boot sequence if you press the ESC key. 

If your hardware checks out, then It's PROBABLY a software bug in Google Earth, Ubuntu, and/or your video drivers.

---

### Post by machavillain on 2007-07-27
I've run Google Earth in Windows without a problem, so I suspect this is a software problem.

---

### Post by Dubbayoo on 2007-07-28
I'm having the same problem with the free ATI driver on Feisty. It worked fine until I upgraded from edgy.

---

### Post by Paulmd on 2007-07-29
> **machavillain said:**
> I've run Google Earth in Windows without a problem, so I suspect this is a software problem.

Many graphics cards, especially off brand, and/or older do not have linux drivers that support 3d acceleration, which Google earth requires to work well (or overwhelming CPU power).  The proper linux drivers require some hunting. 

Anyway, It's where I'd place my first bet on a works in windows, doesn't work in linux issue.

If you let us know what video card or chip you have, we may be able to point to better (or at least different :) ) drivers, and that MIGHT solve the issue.

---

### Post by machavillain on 2007-07-29
I solved this problem by just going into "Restricted Drivers Management" and installing the listed ATI driver...

---

### Post by Dubbayoo on 2007-08-02
I don't see a way to install anything with that applet. It just lists the vmware drivers. I have restricted-modules installed. I just don't use the fglrx driver. I have a Radeon 8500, which the newest ATI drivers don't support (I think)

[IMG]http://www.dubbayoo.net/files/pics/screenshots/rdm.jpg[/IMG]

---

