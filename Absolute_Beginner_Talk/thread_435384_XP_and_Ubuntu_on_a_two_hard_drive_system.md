---
title: "XP and Ubuntu on a two hard drive system"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by spikester on 2007-05-06
if XP is on the master.Can i put ubuntu on the slave and get a dual-booting system?:confused:

---

### Post by bsell on 2007-05-06
> **spikester said:**
> if XP is on the master.Can i put ubuntu on the slave and get a dual-booting system?:confused:

Yes. You might consider putting the bootloader (GRUB) on the Ubuntu drive.

---

### Post by alienexplorers on 2007-05-06
On the second drive setup 3 partitions:

> ROOT     / 
HOME     /home
SWAP     swap

The advantage of setting up a /home partition is that in case you have to re-install Ubuntu your preferences are saved.

---

### Post by ticopelp on 2007-05-06
Yes. That's actually the way my system is set up. I installed a second HD, put Ubuntu on it, and can now dual-boot. Ironically, I never want to boot into Windows anymore, so I suppose the second HD will just sit and rot now. :)

---

