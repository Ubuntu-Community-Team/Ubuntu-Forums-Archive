---
title: "ATI Rage 128 Pro Ultra TF driver"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by ryn0 on 2006-10-11
OK, ive read allmost all threads about installing and troubleshouting ATI drivers. The problem is that my card is eemingly not supported by any driver at all, what should i do? Please help me, it is the only that i cant do on my on...

---

### Post by ryn0 on 2006-10-11
anybody?:confused:

---

### Post by lemonsCC on 2006-11-04
I have the same card, same problem.

---

### Post by guysmiley25 on 2006-12-29
Same here!!! Anyone?

---

### Post by GrahamPR on 2006-12-29
bump because I think this might be causing me problems. :(

---

### Post by az on 2006-12-29
The ATI rage 128 is supported by the native ATI driver.  If it only has a small amount of ram, you may need to reconfigure X to use less of it so that DRI (hardware acceleration) is enabled.  You may need to lower your resolution or color depth.

By default, Ubuntu uses the maximum resolution and color depth.  Even if you switch down to a lower resolution, the ram is not freed.

You need to boot into recovery mode and run

dpkg-reconfigure xserver-xorg

and try using 1024x768 at 16-bit for a card with 16 megs of ram, for example.  If your card has less ram, you need to go even lower.

---

