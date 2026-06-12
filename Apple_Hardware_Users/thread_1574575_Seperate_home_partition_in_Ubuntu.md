---
title: "Seperate home partition in Ubuntu"
date: 2010-09-14
forum: Apple Hardware Users
---

### Post by Engine_number_9 on 2010-09-14
Later this week I'll be making a fresh install of Ubuntu on a MB 5,1. I'd like to have a seperate home partition in a dual boot setup with OS X and Ubuntu. Can I make a seperate home partition during installation the same way as I would if I had a PC dual booting Windows and Ubuntu?

---

### Post by srs5694 on 2010-09-14
In principle, yes. Be aware, though, that the usual instructions for installing Ubuntu on Intel-based Macs involves use of a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration. Although Linux is quite happy to use a pure-GPT setup, there seem to be some extra hoops to jump through to get this to work on a Mac. (I don't have an Intel-based Mac to experiment with, so I can't offer much advice on how to get this to work.) My suggestion, based on my limited knowledge, is to ensure that the Linux root (/) partition and the OS X boot partition both end up in the hybrid MBR. The usual tools just dump the first three GPT partitions, aside from the EFI System partition, into the hybrid MBR, so put them both there and hope for the best.

---

