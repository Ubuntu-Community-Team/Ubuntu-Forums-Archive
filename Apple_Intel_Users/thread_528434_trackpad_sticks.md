---
title: "trackpad sticks"
date: 2007-08-17
forum: Apple Intel Users
---

### Post by xIke on 2007-08-17
My trackpad works great except when I try to drag something.  Then it works at first, but sticks.  It seems like every other drag with my finger isn't recognized.  Anyone else having any trackpad issues?

Thanks,
-xike

---

### Post by cyberdork33 on 2007-08-17
please tell us what machine you have (and the generation) as well as what version of ubuntu.

There have been a few issues with the touchpads for the most part, but most are being resolved. Try looking here:
[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

---

### Post by xIke on 2007-08-17
I'm sorry- I should have included that info.

I have a MacBook Pro, bought it spring of this year.

---

### Post by cyberdork33 on 2007-08-17
Santa Rosa?
[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by xIke on 2007-08-17
I guess...how do I find out if it's a SantaRosa?  Also, I didn't see anything in that thread (I looked through all 21 pages) that would help...

---

### Post by cyberdork33 on 2007-08-18
> **xIke said:**
> I guess...how do I find out if it's a SantaRosa?  Also, I didn't see anything in that thread (I looked through all 21 pages) that would help...

what graphics hardware is it?

The guys that respond in that thread will be able to help with problems on Santa Rosa hardware. There were some having issues with odd trackpad behavior. I don't know if there is a solution yet.

---

### Post by xIke on 2007-08-18
ATI Radeon x1600

---

### Post by cyberdork33 on 2007-08-18
> **xIke said:**
> ATI Radeon x1600
OK, not Santa Rosa.
If the Synaptics thread is not helping, the only other thing I can suggest is messing with the mouseemu module. Try unloading it with:
```
sudo modprobe -r mouseemu
```

If that doesn't help matters, I don't know what to tell you.

---

### Post by xIke on 2007-08-19
I don't have that, so I guess no luck.  Thanks anyway.

---

### Post by macbookmaster on 2007-08-21
u can get an external mouse for like 10 bucks man,  but i dont have this problem on my mb

---

### Post by xIke on 2007-08-21
I have a Razer Diamondback.

However, this is a laptop and occasionally used as such (without other stuff plugged in.)

---

