---
title: "Gparted help"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-03
Ok, my install keeps hanging at partitioning, not even giving me an option. I now have Gparted Live booted up. I do not want to dual boot, and will use the entire drive for Ubuntu. I haven't found anything that gives specifics on any optimum partitioning. Any ideas?

---

### Post by Gannin on 2006-05-03
The simple way is to make two partitions.  A big one for / (root) where all of your files will go, and another one for swap, with perhaps 10% of the drive space being used for swap.

Another option is to have three partitions.  A decent-sized one for / (root), then another big one for /home, then a third for the swap partition.  That way, if you install a new system, you can have it overwrite your / (root) partition, thereby giving you a new system, but leave all your personal files in /home alone, so backing everything up doesn't become as much of an issue.

---

### Post by bt224 on 2006-05-03
Well, I went for 1 big partition. It's a 6G hard drive and I won't be running anything else on the unit. It's my old, old work computer that IT decided was past it's lifespan, so I got it for free. I think I pushed enough buttons to get something to work, it now says Base is installing. Keep your fingers crossed.

---

