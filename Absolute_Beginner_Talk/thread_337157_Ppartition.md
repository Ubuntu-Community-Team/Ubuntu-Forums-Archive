---
title: "Ppartition"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-12
Asked this a while ago but still having difficulties runnibg the installation, the liveCD wont partition my drive so trying to do it myself. can someone tell me the types for the two partitios, as in fat32 or what? any help much appreciated, thanks.

---

### Post by zerhacke on 2007-01-12
Linux is traditionally installed with EXT2 or EXT3 filesystems, though there are many other types you *could* install to.  Stick with these two types and you'll do fine.

---

### Post by taurus on 2007-01-12
For Ubuntu, use ext3 for / and swap for swap.  Please don't install Ubuntu on fat32 because you will run into all kind of problems later (real soon).

---

### Post by john.n on 2007-01-12
Whats the size of the swap partition meant to be?

---

### Post by Bachstelze on 2007-01-12
It depends on how much RAM you have. If you have 1 GiB or less, twice your RAM is a good compromise. If you have more, you can go with a swap of 512 MiB if you don't plan to use suspend-to-disk.

---

