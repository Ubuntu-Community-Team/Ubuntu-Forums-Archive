---
title: "take space from ubuntu partition for winxp"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-12-26
I have found a few threads that address going in the opposite direction, but here's what I need:

I initially partitioned roughly 6.7 gigs for windows, I set my box up for dual boot and currently still have 4.9 gigs of free space in ubuntu. I have 324 megs free in windows. 

I intended to use a lot of that space for music because I just got a Creative zen v mp3 player. 

When it is hooked up to mu usb port, ubuntu can't see it, and I have tried for the last two days to get it to work. 

I booted in windows, and it's greased lightning. So, what I need to do is transfer all that space to my windows partition so it will be usable. Is there any way to do this? If not, I'll just format out my ubuntu partition as a 'd' drive for windows, but prefer not to eliminate ubuntu entirely. any suggestions would be appreciated.

---

### Post by patrickaupperle on 2007-12-26
Try using GParted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

run it from live cd

If your windows partition is NTFS it should work, according to wikipedia anyway.

good luck:)

---

### Post by LaRoza on 2007-12-26
GParted, see the link in my sig.

Do not just delete the Ubuntu partitions, Windows won't boot. Use the Super Grub Disk (also in the link in my sig) to restore the Windows MBR.

Advanced->Windows (Advanced) and restore, I think it is the first option.

I am not saying to do this, but if you do get rid of Ubuntu, make sure you have the SGD handy.

---

