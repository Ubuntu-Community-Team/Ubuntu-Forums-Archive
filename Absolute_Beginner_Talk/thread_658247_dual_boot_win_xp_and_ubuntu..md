---
title: "dual boot win xp and ubuntu."
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by umfufu on 2008-01-04
Hello ,

i would like to install to install the ubuntu live cd on my computer.

Probably it is going to work all fine but i need to ask a few questions before installing.

I have 2 sata hard drives 250 Gig, on 1 xp and the other i would like to install ubuntu.

What is the best way to install, i still need to use xp sometimes so i would like to choose?

regards.

---

### Post by pieterjanvu on 2008-01-04
Install xp before ubuntu, then run the live cd. in the install procedure you get the oppurtunity to choose which harddrive to install to or partition. The install configures grub to include other OS like XP. Grub is the bootloader that ubuntu uses by default and it should automatically have xp configured so that you can choose which OS to boot. I haven't had personal experience with 2 harddrives, but have partitioned and dual booted

---

### Post by Razorback on 2008-01-04
Install Ubuntu on the other drive then choose to boot that drive first.  You can then modify Grub (bootloader) to allow you to choose which OS to boot from its menu.  That is what I do and it works great.

---

