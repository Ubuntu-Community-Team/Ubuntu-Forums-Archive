---
title: "Installation problems(ITE ATA Controller + Marvell LAN)"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by metty on 2005-10-04
Hi Ubuntu-Freaks(or whatever ;) )!

1.) Sorry for my bad English, but I hope, you'll understand!
2.) Now my problem:
I can't install Ubuntu 5.0.4 because the installer can't find a driver for my ATA IDE Controller:
- ITE IT8212 ATA RAID controller

Is there an solution? Maybe 5.10? And you shouldn't come with kernel compiling or such things, because i'm a beginner, sorry!

3.) Also i have problems with the LAN! Here's the name of it:
- Marvell Yukon 88E 8053 PCI-E Gigabit Lan

The installer tells me, there is nothing like a lan card found in my system, but in Windows(don't bet me) it runs perfect!

So it's maybe not easy to understand me, but all in all I think you can help me, please!

Metty

---

### Post by Dark79 on 2005-10-17
Sorry, Breezy won't find your ITE controller either, which really bothers me considering the popularity of the it8211/it8212 controller on modern boards. That and the fact that other distros have been offering patched version with driver support :???: 

I won't tell you to bother with compiling kernels, not because you're a beginner but because it hasn't worked for me yet :( 

Looks like I'm stuck with Windows XP on my desktop for the time being...

EDIT: My motherboard also has a Marvell Yukon Gigabit LAN adapter (88E 8001), and Breezy finds it, and recognizes it, but for some reason it wouldn't work. Ended up sticking with my Intel Pro Gigabit LAN adapter instead. Maybe you might have better luck, but I guess it wouldn't matter much if you can't get your hard drive working.

---

