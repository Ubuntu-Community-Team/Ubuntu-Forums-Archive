---
title: "Odd start-up sequence on 7.10"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by tall8 on 2007-12-10
The following is the identical start-up sequence which has occurred for days, after which the laptop operates normally (apart from a random shut down problem which seems to have gone after I changed the power settings to hibernate after 30 min. of non-use):

checking root file system
fsck./40.2 (12 Jul 2007)
dev/sda4 has gone 1284 days without being checked, check forced

Then something is being checked with percentages through 100% being shown, a further start-up sequencing occurring and the normal sign-in screen appearing.

Anyone know what's happening? Thanks. Despite these puzzlements, the 7.10 is a great system, far superior to Windows XP..

---

### Post by Ferri on 2007-12-10
Ubuntu checks your hard disk every 30 times it's mounted. It should'n happen next time you boot up.

---

### Post by tall8 on 2007-12-10
That's really great.Unlike with Windows which must be deliberately done and is a far lengthier procedure.

---

### Post by Sef on 2007-12-10
> Ubuntu checks your hard disk every 30 times it's mounted. It should'n happen next time you boot up.

Not quite.  It's ext3 that checks itself every 25-30 times that it boots up.   If you choose reiferfs then you never encounter that since it never fragments.   Ext3 can fragment, but problems are very rare with it, unless the hard drive gets at least 90% full.

---

