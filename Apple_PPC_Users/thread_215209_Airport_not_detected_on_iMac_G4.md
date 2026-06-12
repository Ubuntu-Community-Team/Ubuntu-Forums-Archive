---
title: "Airport not detected on iMac G4"
date: 2006-07-13
forum: Apple PPC Users
---

### Post by king_arthur on 2006-07-13
Much to my regret, my (standard) Airport card is not being detected by the Dapper CD on my iMac G4-flat screen. :(

It used to work very well however, including WEP encryption, with the Breezy-ppc live CD on the same computer.

I wonder if anybody else is experiencing the same problem and has found a workaround.

What a pity... 

/P

---

### Post by king_arthur on 2006-07-13
Well, this was easier than I thought... :D

**$sudo modprobe airport** did the job.

I can even use 128 byte WEP encryption.

Nice :D

/P

---

