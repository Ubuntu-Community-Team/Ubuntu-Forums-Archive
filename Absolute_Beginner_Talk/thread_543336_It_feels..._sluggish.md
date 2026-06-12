---
title: "It feels... sluggish :/"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-09-05
I replaced the motherboard, cpu, and ram of this pc with newer components, although on the cheaper side. AMD Sempron 3400+ and a VIA chipset & Integrated graphics with 512MB ram. I had thought that would be overkill compared to what this PC is meant for... light web surfing and word processing.

For some reason, the old Pentium 4, 256MB ram components with Intel graphics it is replacing seemed quicker than this. I hope maybe this is just a driver thing because Knoppix was having trouble transferring files to a USB drive. It would slow down, stall... then start and stall etc. Very slow for a 200MB transfer. There is always 5% of cpu in use when system monitor is on, simply clicking and dragging a box on the screen around can lead to 100% cpu if you move the mouse around constantly.

Current Specs:

AMD Sempron 3400+ Socket AM2, 1.8Ghz
512MB DDR2 ram (forgot speed)
1.2 GB swap (it defaulted that much)
40GB hard drive
VIA integrated graphics (it is a K8M800 chipset)

---

### Post by Darklighter137 on 2007-09-05
This may not be terribly helpful, but I've found that sometimes brand new components take a bit to get "broken in", so to speak.

---

### Post by zero-9376 on 2007-09-05
what driver are you using for the graphics in xorg? i had high cpu usage when using vesa on my via based laptop

---

### Post by fastpakr on 2007-09-05
> **Darklighter137 said:**
> This may not be terribly helpful, but I've found that sometimes brand new components take a bit to get "broken in", so to speak.

Wow.

---

### Post by kavon89 on 2007-09-05
> **Darklighter137 said:**
> This may not be terribly helpful, but I've found that sometimes brand new components take a bit to get "broken in", so to speak.

Maybe for cooling, but definatly not for performance.

> **zero-9376 said:**
> what driver are you using for the graphics in xorg? i had high cpu usage when using vesa on my via based laptop

Whatever is set by default is what I am using. Sounds like I need drivers to fix this issue. Anyone know where I can get them??

---

### Post by banewman on 2007-09-05
Did you keep the hard drive as it was - straight from the pentium computer into the amd?

---

### Post by igknighted on 2007-09-05
> **kavon89 said:**
> Maybe for cooling, but definatly not for performance.



Whatever is set by default is what I am using. Sounds like I need drivers to fix this issue. Anyone know where I can get them??

Intel graphics (like on your old board) tend to perform very well in linux.  Via, on the other hand, do very very poorly.  If you are going to continue to use the via board, I would look for a cheap ($10-$15 is all you would need) graphics card (nvidia).

---

### Post by kavon89 on 2007-09-05
All I have is a Radeon 7000 PCI, 64MB. It did pretty decently with Mandriva last time I used it. Would that be better than the VIA graphics?

> Did you keep the hard drive as it was - straight from the pentium computer into the amd? 

No, I erased Windows XP and installed a fresh Ubuntu.

---

### Post by asmoore82 on 2007-09-05
> **igknighted said:**
> Intel graphics (like on your old board) tend to perform very well in linux.  Via, on the other hand, do very very poorly. ** If you are going to continue to use the via board, I would look for a cheap ($10-$15 is all you would need) graphics card (nvidia).**

I second that, your computer is already as fast as it can be,
but the VIA Xorg drivers are client/server with network transparency ...
in other words the computer computes very quickly but the display is not keeping up with it.

A cheap nVidia card (GeForce2 MX400 or higher) will make your computer **feel** 20 times faster;
simply because the Graphics will keep up with the computing more, especially
if you choose to use nVidia's proprietary driver.

---

### Post by n3tfury on 2007-09-05
> **fastpakr said:**
> Wow.

lol

---

### Post by ahale1987 on 2007-09-05
Yes, the card would be better than the onboard video. Video was never VIA's strongpoint

---

### Post by kavon89 on 2007-09-05
Hum, should I install it, disable the onboard video in the BIOS, then let it boot and auto-reconfigure, or should I reinstall? It is a literally fresh install so I don't mind reinstalling it again.

---

### Post by Hobo Joe on 2007-09-05
You don't need to reinstall, you can use Envy to install drivers.

When you install the new card, from recovery mode, type:
```

sudo dpkg-reconfigure xserver-xorg

```
And set the driver to vesa. Then restart and install Envy. I have a link in my sig.

---

### Post by ahale1987 on 2007-09-05
no need to reinstall. Just disable onboard video via BIOS and let the system see the new card

---

