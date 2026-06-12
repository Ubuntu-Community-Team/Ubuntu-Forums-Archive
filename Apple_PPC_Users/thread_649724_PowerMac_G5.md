---
title: "PowerMac G5"
date: 2007-12-25
forum: Apple PPC Users
---

### Post by michaeljbergin on 2007-12-25
I'm hoping to get some general information on how well the PowerMac G5 is supported by Ubuntu.  I know there is an ISO for PPC but I'm hoping to use this as a recording workstation, hopefully as good or better than OS X/GarageBand.  I tried with my MacBook Pro and its just not possible due to lack of support for the sound card, undocumented apparently.  Aside from recording Ubuntu works great on my MacBook Pro so I'm hoping I can use my G5 instead.  I don't need any specific guidance just some yay/nay from a few people who have done it.  Thanks.

---

### Post by stmiller on 2007-12-25
Hey I'm a music composer, and had a Powermac G5 dual 2Ghz running Ubuntu. (Recently sold that machine, though.) I had to install with the PowerPC alternative CD, as the live Ubuntu PPC CD did not boot.

For audio apps it was solid, and jack supports the onboard audio of Powermac G5s with the snd-aoa driver nicely. A compatible firewire device from the ffado project might be a better option though, depending on your needs. Linux supports all of the hardware of the Powermacs, including all processors, as much ram as you have, and so forth.

I mainly used Ardour + Rosegarden and all of the usual soft synths. There are some nice EQ and reverb plugins for Ardour out there.

The only cons are that 3D acceleration works with ATI based video cards, but not with the Nvidia based ones, if that is a factor. And sleep is supported only with ATI based radeon cards as well with a recent kernel.

---

