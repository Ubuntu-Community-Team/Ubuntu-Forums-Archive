---
title: "Mac Book Pro Help!!!"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by TattooedRunes on 2008-04-14
ok... So, I'm trying to help a buddy dual-boot gutsy and leopard on his macbook pro, and I tried to do it the same way I did it to dual boot my vista machine.  No go.  We used gparted to hammer out the ext3 and swap, installed the standard way, and watched it install just fine.  Here's the problem... grub doesn't load on reboot... it goes straight to leopard every time... when I installed Ubuntu on my system (I've done it twice now), grub is up and running immediately.  What did we miss?

---

### Post by estaticd on 2008-04-14
If you installed rEFIt, you should have a choice between booting OS X and Ubuntu. Use the arrow keys and Enter to select Ubuntu. 

See:  [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by TattooedRunes on 2008-04-14
ok, we're going to try this... let you know

---

### Post by TattooedRunes on 2008-04-14
ok, we did this, installed rEFIt and it seems to look great... it gives us two options for a Linux boot... but this is what we get: a black screen with

GRUB_





and nothing...

ooh just restarted again and we've got a grey screen with Tux in the middle... again not doing anything.

---

### Post by TattooedRunes on 2008-04-14
ok, now we tried the alt/option method of booting and it's right back to the black screen with 

GRUB _

on it... wtf?

---

### Post by estaticd on 2008-04-14
I'm not a mac genius or anything here, so please take this with a grain of salt... hopefully someone else can chime in here and confirm my thoughts.

This might be a problem with GRUB not being able to load the kernel because it's in a partition past the first 2GB of the drive, it seems pretty similar to what other people see in that sitsuation.

What might need to happen is creating a very small (50MB) /boot partition to load GRUB and the kernel image from at the beginning of the drive, then have you Mac partition, then the ubuntu partition after that.

I think step 6 ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) is what we're missing, the partition scheme is not letting GRUB properly boot the machine.

---

