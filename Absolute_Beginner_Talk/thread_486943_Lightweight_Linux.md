---
title: "Lightweight Linux?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by kungfugecko on 2007-06-28
Alright, So I'm running some older hardware (733mhz Pentium III, 256mb RAM, 20GB HDD)

I put Ubuntu on, and it ran fairly slow.  I read that Xubuntu and xfce desktop (sp?) ran a little faster on older machines, so I gave it a whirl, but it's still not performing quite up to what I had hoped.  Should Xubuntu be running OK on my hardware?  Are there any speed tweaks?

What would be an alternative to Xubuntu, that would run faster? I've done some research and seen "Vector Linux" and "Damn Small Linux" come up a few times while searching for a fast linux on older hardware.  Any opinions on these and/or what version of these would work?

Thanks for your thoughts!

---

### Post by bodhi.zazen on 2007-06-28
Puppy Linux or Zenwalk

---

### Post by Inxsible on 2007-06-28
> **bodhi.zazen said:**
> Puppy Linux or Zenwalk
I came in to say the exact same thing. Puppy Linux has a pretty small footprint

---

### Post by Terry of Astoria on 2007-06-28
I have a few machines of that caliber. They really work a lot smoother when you get above 256 megs. Try to upgrade your RAM. It should be relatively cheap. Seems like any machine with that proc ought to be able to eat more RAM. Have you any open RAM slots? A computer shop would probably sell you a chip or two.

---

### Post by John.Michael.Kane on 2007-06-28
You can use one of these routes which would give you flux on ubuntu Or you can try Puppy Linux Zenwalk Damn Small Linux.

[How To: Create a lightweight installation]("http://ubuntuforums.org/showthread.php?t=325042&highlight=fluxbox")

[Fluxbox installing]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by tarek on 2007-06-28
My friend has 256mb ram and he's using Ubuntu. He says it's not bad.

Have you tried fluxbox? It's lighter than Xfce. To install it run the following command: sudo aptitude install fluxbox

TK

---

### Post by notwen on 2007-06-28
+1 on Flux on top of Ubuntu 

or

+1 on Puppy Linux

---

### Post by kungfugecko on 2007-06-28
OK, based on the replies, I'm gonna give "fluxbox" a shot, then if that still proves too slow for my tastes =P I'll give puppy Linux a shot

Thanks guys

---

### Post by tarek on 2007-06-28
Just curious is puppy linux baesd on debian?

---

### Post by chandler on 2007-06-28
I would agree with the RAM upgrade, even just an extra 256 will make a huge difference.  Fluxubuntu ran just fine in a VM with limited 256 so maybe there's something else that's eating up the RAM?  Try running top and watch the memory usage and post what's eating it all.  A quicker way to do it is with this:
```
ps aux | awk '{print $4 " " $11}' | sort -n
```

Just run it when it's slow...


For the poster above: "Puppy Linux is not derived from another distribution. It has been built from the ground up by Barry Kauler. Unlike most of the Linux distribution developers, Barry hails from Australia. During more recent times the Puppy community, represented by the obligatory forum, has aided Barry to introduce some wonderful ideas which results in the latest 1.0.7 version."

---

### Post by kungfugecko on 2007-06-28
from this thread: [http://ubuntuforums.org/showthread.php?t=281922](http://ubuntuforums.org/showthread.php?t=281922)

it appears that it is not based on debian

---

### Post by tarek on 2007-06-28
Thanks chandler.

You can also use: top

---

### Post by notwen on 2007-06-28
> **tarek said:**
> Just curious is puppy linux baesd on debian?

Pretty sure Puppy Linux is built from scratch and has it's own package managers, PupGet and DotPup.  I've use it here and there for a LiveCD session.  It''s quality stuff. =]

---

### Post by Lord Illidan on 2007-06-28
Damn Small is based on Debian, AFAIK.

---

### Post by chandler on 2007-06-28
Top is good but it could draw more resources and slow it down even more.  Also, it could be distracting/hard to understand if he's relatively new.

---

### Post by RedSquirrel on 2007-06-28
> **kungfugecko said:**
> Alright, So I'm running some older hardware (733mhz Pentium III, 256mb RAM, 20GB HDD)

I put Ubuntu on, and it ran fairly slow.  I read that Xubuntu and xfce desktop (sp?) ran a little faster on older machines, so I gave it a whirl, but it's still not performing quite up to what I had hoped.  Should Xubuntu be running OK on my hardware?  Are there any speed tweaks?

What would be an alternative to Xubuntu, that would run faster? I've done some research and seen "Vector Linux" and "Damn Small Linux" come up a few times while searching for a fast linux on older hardware.  Any opinions on these and/or what version of these would work?

Thanks for your thoughts!

I am a little surprised Xubuntu didn't work that well on your hardware. I have tried it on a 600 MHz AMD Duron with 320 MB RAM and a 32 MB video card and it was quite responsive.

In any case, here are some more links for you...

If you want to stick with Ubuntu, you can do a barebones install and add only the things you need. That will help you get the most out of your hardware and still use Ubuntu which has this nice community. :)

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

If you plan to use Fluxbox, some of the links in my signature may be of help.

Have fun. :D

---

### Post by izizzle on 2007-06-29
Yoper might possibly run fast on your computer. Although it uses KDE, it has proven to run very fast on older hardware. I suggest you try it.

---

