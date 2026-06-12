---
title: "Intel 945G+ICH7 chipset."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-03-07
I am trying to set up a new install on a machine with an Intel 945G+ICH7 chipset installed.
It took over two hours via the Live CD to get a running installation. 
Someone suggested the chipset might be the problem of a slow running machine, as the cd-rom was painfully slow.
I did try using the Gparted disc as I wanted to remove Windows completely but it failed to run beyond a start screen.
I am a relative newbie and would appreciate some help.

---

### Post by newbeeman on 2008-03-07
Bump

---

### Post by tgalati4 on 2008-03-07
Gutsy runs fine on a desktop machine with Intel 945G and ICH7 chipset.  If you have Windows NTFS partition on a disk drive, it could be slowing down the system, especially if there are errors on the Windows partition.

Go through dmesg and cut and paste stuff that looks suspicious and post it here.

> dmesg | more

These forums get busy, so don't expect an answer within an hour.  Generally you'll have to wait a few hours for posts to roll in.

---

