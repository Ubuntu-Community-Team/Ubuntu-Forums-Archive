---
title: "cpu inefficient gui?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by at0mic on 2006-11-14
hi,

wondering why i cant move windows around [circular motion or whatever] rather fast without it chunking up? i have a athlon64 /w 2GB RAM... does everyone experience this? if everyone experiennces i think it should be addressed. im now on kbuntu and ubuntu had the same issue... least with 6.10. installed the nvidia 6600 driver as well....

---

### Post by szf on 2006-11-14
> **at0mic said:**
> wondering why i cant move windows around [circular motion or whatever] rather fast without it chunking up? i have a athlon64 /w 2GB RAM... does everyone experience this?

I experience this - but xorg is actively working to reduce/remove this (was is K. Packard who said "double buffering everywhere" not so long ago?).

> **at0mic said:**
> if everyone experiennces i think it should be addressed.

Good. Get involved.


> **at0mic said:**
> im now on kbuntu and ubuntu had the same issue... least with 6.10. installed the nvidia 6600 driver as well....

IMO, Ubuntu has been pretty good in this particular area - and 6.10 is my rev. I use a Pentium 4, pre-HT, with a nvidia 6200 AGP card and fault no one on performance.

---

### Post by jordanmthomas on 2006-11-14
It might be a little extreme, but you could install beryl or compiz.  Everything is drawn as a texture when moving, so there is no redrawing of windows behind the one you're moving.

---

### Post by at0mic on 2006-11-14
> **szf said:**
> I experience this ... and 6.10 is my rev. I use a Pentium 4, pre-HT, with a nvidia 6200 AGP card and fault no one on performance.

If MS can get it right... ud think the linux master jedis could :)


makes me wonder if this problem exists on other linux distros and / or previous versions of ubuntu

---

### Post by at0mic on 2006-11-14
thnx for the suggestion... i tried compiz from the repository... ran it with --replace option... crashed the desktop engine completely.

---

### Post by szf on 2006-11-14
> **at0mic said:**
> If MS can get it right... ud think the linux master jedis could :)

I disagree in that the Xorg team has provided something * quite good *, and provided it under a MIT-license. Xorg is not linux-centric (AFIK), either - so improvements made extend throughout the *nix universe.

> **at0mic said:**
> makes me wonder if this problem exists on other linux distros and / or previous versions of ubuntu

You may not find a fault-proof distro in this regard. I've experienced visual-chunkiness when moving windows to a greater-or-lesser degree since '99. Now it is greatly reduced, and I am thankful for the work of those developers...

---

