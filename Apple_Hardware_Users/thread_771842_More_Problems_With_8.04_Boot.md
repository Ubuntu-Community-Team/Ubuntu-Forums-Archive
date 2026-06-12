---
title: "More Problems With 8.04 Boot"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by Teh Dust on 2008-04-28
I am using a Mac Book Pro (model before santa rosa, I believe gen 2?)

I set aside 50gb of space for ubuntu using bootcamp.

I deleted the third partition and made 49gb of ext3 for the root and left the other gig to be used as SWAP.

I went thru the installer and set GRUB to install its self onto the third partition (ubuntu root)

I installed rEFIt and attempted to boot into ubuntu and got the no bootable devices error.

I synched the mbr and now when I select to boot from ubuntu, the loader stalls at the tux logo.

What have I done wrong?

---

### Post by cyberdork33 on 2008-04-28
> **Teh Dust said:**
> I am using a Mac Book Pro (model before santa rosa, I believe gen 2?)

I set aside 50gb of space for ubuntu using bootcamp.

I deleted the third partition and made 49gb of ext3 for the root and left the other gig to be used as SWAP.

I went thru the installer and set GRUB to install its self onto the third partition (ubuntu root)

I installed rEFIt and attempted to boot into ubuntu and got the no bootable devices error.

I synched the mbr and now when I select to boot from ubuntu, the loader stalls at the tux logo.

What have I done wrong?nothing unfortunately.

try holding the option key on statup and select your device from there.

you are experiencing some new bugs we have recently found...

---

