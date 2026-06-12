---
title: "ALSA detects older chipset than mine"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-11-11
Hi,

My mainboard is the Gigabyte GA-P35-DS3, with a Realtek ALC889-A audiochipset.
I'm experiencing trouble, as is everyone with a Intel HDA compatible card (am I saying it right?),
but I actually got hope when I saw my chip finally gets supported by ALSA. When listening to music with a slow pace and low volume I can hear an irritating noise. Sounds like some sort of breeze of the wind on a synthesizer.

Anyways,
I installed ALSA from source, as described by some tutorial which I'm pretty certain is reliable. I believe the installing procedure was standard, involving './configure' , 'make' and 'make install',
so therefore nothing actually could have gone wrong.
When I opened Alsa Mixer it showed the correct version, which is 1.0.15. Therefore I'm pretty sure everything worked out. I switched to the ALSA HDA Intel driver in my Gnome mixer,
but I found out (running Alsamixer) that it's (still, as before update) using Realtek ALC885.
I want it to use ALC889-A which it now supports!

I don't know it that would fix my problem, but I'd sure like to try.

So basically: how can I take care of ALSA choosing the ALC889-A module instead of the ALC885 module?

Thanks :)

---

### Post by bartkl on 2007-11-12
no one?

---

### Post by causticburning on 2008-04-10
I am having a similar problem.  Although, it doesn't seem to be breaking too much using the 885 driver?  But then again I'm still setting up ubuntu so I won't know for a little while.  5.1 seems to work as of the new driver release.

---

