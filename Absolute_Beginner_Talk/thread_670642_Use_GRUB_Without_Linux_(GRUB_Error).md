---
title: "Use GRUB Without Linux (GRUB Error)"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by freebullets on 2008-01-17
I recently installed Ubuntu, but I uninstalled it soon after since it was ******* up, and I didn't like it.  I uninstalled it by deleting the Linux partition, but I had this setup:

160GB SATA: Vista Partition and Linux Partition
33GB IDE: XP Drive

For some reason, Linux installed GRUB onto my XP drive, so now when I try to boot from my XP drive, GRUB gives me an error, probably since I deleted the Linux partition.  Also, Vista's bootloader won't boot XP.

So, what I'm asking is, Is it possible to either uninstall GRUB or configure it to use without Linux?

---

### Post by dcstar on 2008-01-17
> **freebullets said:**
> 
..........
For some reason, Linux installed GRUB onto my XP drive, so now when I try to boot from my XP drive, GRUB gives me an error, probably since I deleted the Linux partition.  Also, Vista's bootloader won't boot XP.

So, what I'm asking is, Is it possible to either uninstall GRUB or configure it to use without Linux?

Do a search for restoring the windows mbr.

---

