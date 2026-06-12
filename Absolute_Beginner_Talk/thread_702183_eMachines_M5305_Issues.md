---
title: "eMachines M5305 Issues"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by pr0me7heu2 on 2008-02-20
So I used slackware when I was in middle school for a bit and decided it was time to return to linux and give it a try.

I have an eMachines M5305 (Specs: With Mobile AMD Athlon XP-M 2200+, 512MB DDR RAM, 15.4-inch LCD (1,280-by-800), ATI Radeon IGP 320M graphics, 40GB hard drive).

I did the live CD and it worked perfectly; however, upon startup I get a blankscreen.  I did a little searching and found that pressing Alt + Ctrl + F1 brings me to the log in...

So I'm looking now to find a way of installing drivers.  I've done endless google searching and I can't find any drivers for the ATI video card (which I am assuming is causing the blank screen - yes/ no?) and I can't find a driver for my old 2wire wireless card.  I'm thinking it'd maybe work if I managed to find a driver for the PCMCIA card.

Any hints at where I should start at?

Thanks!

---

### Post by spiderbatdad on 2008-02-20
There may be a Config Display setting in your bios to fix the problem ie, vga.
Otherwise there are a number of possible fixes for this problem.
Often this is a problem with the settings in /etc/usplash.conf...the resolution is unsupported by your display settings and can be easily fixed.

You can edit the /boot/grub line from the grub screen at start up. And the make the changes permanent in /boot/grub/menu.lst

You can try spamming the esc key every 20 secs. or so and giving usplash 4-5 minutes to start. If the system eventually boots, edit /etc/usplash.conf to 1024x768.

You may need to boot into safe graphics mode and edit /boot/grub/menu.lst to delete ro --quite splash and include noapic vga=792

---

