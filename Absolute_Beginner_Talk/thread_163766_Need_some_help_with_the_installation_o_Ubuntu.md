---
title: "Need some help with the installation o Ubuntu"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Entrail on 2006-04-21
Hi. When I comes to the partitioning I want to have one partition on 20GB which   my computer will boot from and the rest of the disc I will use for storage of files and stuff. 

This is what I would like to know:
-What do I set the partitions to? (like /home, /boot, /...)
-What do I do after the partitioning?

Sorry if there are any spelling or/and grammar mistakes.

Thanks, Entrail.

---

### Post by macdo on 2006-04-21
If you only want 2 partitions + the swap partition, then one should mount at / for the OS, and the other at /home for your home directory. Some people like a separate partition at /boot, which just contains the boot files (half a GiB is about 10 times what you need for that). 

20 GiB is waaaay more than you need for the OS: I'm running mine at not quite 8 GiB, and it's only half-full...

---

### Post by nowadays who knows on 2006-04-21
:-k Try  8gig as root 1 gig as swap and 11gig as home. Be sure that 8 gig is marked as root with boot or youll start all over again afterinstal if bootable is not selected. :KS

---

