---
title: "Dual boot Sata/IDE trouble"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by RAH1 on 2007-02-18
Ran into a little problem. Installed Ubuntu on 
a little IDE hard drive. XP is on Sata Raid 0.

I have read thru the pinned items, and there
are about 10 different versions of what you
should change Grub to.

And with my luck, the one I used didn't work. Now
it boots directly to Win.

I guess the easy way would be to reinstall grub using
the disc. Now which Grub change do I use for it to work?

Used:
title microscoft windows xp home
root (hd1,0)
savedefault
makeactive
map (hd1,hd0)
map (hd0,hd1)
chainload +1

Thanks

---

### Post by confused57 on 2007-02-18
You could try:

title   microscoft windows xp home
rootnoverify  (hd1,0)
savedefault
makeactive
map  (hd0,hd1)
map  (hd1,hd0)
chainloader  +1

---

### Post by matt8534 on 2007-03-01
I have the same setup and running into problems.  Have you resolved this issue???

---

