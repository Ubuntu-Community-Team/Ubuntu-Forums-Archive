---
title: "Stuck Within Ubuntu Live CD"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Joe325 on 2007-05-09
HI,

This is my first post to anything but since I started using Ubuntu a few months back on my desktop, Im loving it. Anyway, I wanted to try it on my laptop.
I insert the CD to try a live run of it to make sure all my laptop hardware works. Once the ubuntu splash screen disappears, I hear the ubuntu theme sounds , like its starting up,but my laptop doesnt display the screen.
Ive tried with 6.06 and 6.10 but both 'stop responding' at the same point. Ive left it on to see if it was just a delay but nothing happened. Even to eject the CD, I had to hold the power button to turn off and remove CD on next reboot.
My laptop is a Excel D410J which uses Unichrome Pro/VIA chipset graphics card, Sempron 2600 CPU, 1Gb RAM, K8N800 board. 
Any help is appreciated....

---

### Post by viciouslime on 2007-05-09
> **Joe325 said:**
> HI,

This is my first post to anything but since I started using Ubuntu a few months back on my desktop, Im loving it. Anyway, I wanted to try it on my laptop.
I insert the CD to try a live run of it to make sure all my laptop hardware works. Once the ubuntu splash screen disappears, I hear the ubuntu theme sounds , like its starting up,but my laptop doesnt display the screen.
Ive tried with 6.06 and 6.10 but both 'stop responding' at the same point. Ive left it on to see if it was just a delay but nothing happened. Even to eject the CD, I had to hold the power button to turn off and remove CD on next reboot.
My laptop is a Excel D410J which uses Unichrome Pro/VIA chipset graphics card, Sempron 2600 CPU, 1Gb RAM, K8N800 board. 
Any help is appreciated....

Have you tried 7.04? Failing that it sounds like this is a case for the alternate install. If you download the alternate cd then that should work :)

---

### Post by RedSquirrel on 2007-05-13
Try the alternate CD. This guide may also be helpful:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by hairywombat on 2007-12-31
Hi Joe325

I noticed we have the same problem and I was wondering if you'd discovered a solution. I also have a D410J with the same symptoms. I can get at least get the desktop visible by changing to the "vesa" driver in xorg.conf but then I don't have any 3D acceleration.

Cheers,
Wombat

---

### Post by Joe325 on 2008-03-03
Hey Hairywombat,

Sorry its been a while.
I managed to install feisty from an original image, but had to run it in safe mode. Your right though, this via chipset uses the openchrome driver, and from lots of research on the net, openchrome doesnt support 3D. So either we make do or sell our laptops :(

---

### Post by northern lights on 2008-03-03
Oye,

the current stable is 7.10/Gutsy.

Can you post the output of ```
lspci -v | grep VGA
``` Thank you.

---

