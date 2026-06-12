---
title: "No sound with HP Pavilion dv2100 CTO"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Crakkerjakk on 2007-07-24
Howdy folks,

Brand new Feisty Fawn user here.  Having problems with a fresh install(a day old).  I get no sound from my speakers.  I've checked alsamixer to make sure I'm not muted, and followed the directions in this post

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

to the best of my ability.  

When I type lspci in the terminal I get that I have a 'Intel Corporation 82801G (ICH 7 Family) High Definition Audio Controller (Rev 02)

When I enter  sudo lshw -class sound

I get 

  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: iomemory:d4340000-d4343fff irq:23

Now, I've tried the ALSA Driver Compilation step and it failed during the compilation step where you type in sudo module-assistant a-i   alsa-source.  I was hesitant to mess with the kernel, as I'm working from a fresh install (which theoretically means it's not due to something I screwed up in the five minutes I've been using Linux) and I'm new, so I don't wanna muck around with something thats running my machine.  I think thats what the kernel does, right?

I managed to resolve my wireless problem yesterday without adding to the "Waghhh.. my laptop doesn't work" posts, but I'm not seeing as many posts dealing with the issue in this case.  I saw that some people mentioned editing some /etc/modprobe.d/alsa-base(I think) file to include a line saying something about hp, but I'm unsure exactly how to do that or whether it's what I should be doing, since I couldn't find the file they were talking about.

Anyways.  Hopefully thats enough info to convince y'all that I actually looked for a solution before posting and to give y'all some idea of how to fix the damn drivers.  Look forward to your input.

---

### Post by Crakkerjakk on 2007-07-24
bump

---

### Post by ReaderRat on 2007-07-24
Have you enabled the on-board sound in the BIOS?

---

