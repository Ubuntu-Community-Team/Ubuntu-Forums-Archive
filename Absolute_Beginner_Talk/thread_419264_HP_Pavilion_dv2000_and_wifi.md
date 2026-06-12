---
title: "HP Pavilion dv2000 and wifi"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Musmanno on 2007-04-22
Hey guys.  Question from a Linux Newbie (thus the post in this forum) trying to make the switch over from Windows Vista.

I was able to install Linux on my laptop so that I can dual boot into Linux or Vista, with the idea that I can slowly transition to Linux entirely and get rid of Vista at some point.  The only wrench in my plans so far is that I cannot make wireless work.  My HP Pavilion dv2000 uses a Broadcom card, and from what I've been able to gather in various forums, Linux support for these cards isn't so good.

Anyway, I've tried as best I can using ndiswrapper and some windows drivers; I've tried some things with fwcutter; nothing works.  The problem is, my knowledge of Linux is minimal enough that I'm just following online tutorials by rote, not really understanding every step I'm taking, so my ability to tweak the directions for my specific machine is lacking.

Does anyone know of some decent, layman-type instructions for getting this particular wireless card to work?  The driver Windows uses is called BCMWL6.SYS.

Thanks!

Scott

---

### Post by lamalex on 2007-04-22
what is the card chipset? do an lspci and look for the broadcom entry and then post what kind of card it is, then we'll be able to better help you

---

### Post by Musmanno on 2007-04-23
Hey..thanks for the reply.

When I do lspci it says Broadcom Corporation Dell Wireless 1390 wlan mini-pci.

That's the only line that deals with Broadcom.


I appreciate the help!

---

### Post by Musmanno on 2007-04-24
Hey guys...

actually the 64-bit version of SimplyMEPIS detected my card right away.  I am connected to wireless on it right now from the LiveCD (though I had to turn off my encryption temporarily to get it to connect - but that should be fixable from an installed version of MEPIS that can actually remember my WPA key).

Is there any reason not to just use MEPIS at this point?  I'm new to Linux and don't know a whole lot about the differences in distros, but this seems to have most of what I need. 

Thoughts?

---

