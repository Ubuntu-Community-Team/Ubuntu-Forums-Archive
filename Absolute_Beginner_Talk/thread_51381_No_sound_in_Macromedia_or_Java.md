---
title: "No sound in Macromedia or Java"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by AsburyPark on 2005-07-23
I'm sure this is a simple fix, but I cant figure it out.  I have sound on my system.  But when I am in Java sites or Flash sites, no sound.....   What to do? ](*,)

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=AsburyPark]I'm sure this is a simple fix, but I cant figure it out.  I have sound on my system.  But when I am in Java sites or Flash sites, no sound.....   What to do? ](*,)[/QUOTE]

Actually its a big problem...the biggest in Ubuntu currently. To kinda fix the problem use this command:

> killall esd

what you just did is stop the Gnome sound software. ESD is not very good. You will notice that Gnome sounds go away but flash and stuff work fine.

If this bugs you a lot there are some how tos around here to fix it a little....but its a hard problem to fix. I would leave it alone for now (I broke more trying to fix it)

Luckily, this is THE biggest priority in the next release.

---

