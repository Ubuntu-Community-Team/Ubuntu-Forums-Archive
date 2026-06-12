---
title: "Partitioning hard drive for clean install"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-11-09
Hi there, 

Planning on doing a clean install of Ubuntu Breezy Badger on my 160 gig. I have seen a few people on Linux forums say that it's good practice to have three partitions, one for swap, one for system files and one for your data. 

Is this a good idea? What size would I make each of the partitions using a 160 gig? When a new release of Ubuntu comes out would I simply install it to the system files partition?

Any advice would be greatly appreciated.

---

### Post by Pablo_Escobar on 2005-11-09
IMHO that's the best idea.
"\" partition  - mine's 10GB and it'll be more than enough
"swap" partition -  2 x RAM you have on Your PC (mine is 2 x 512 = 1024 :) )
"\home" parition - the rest :D

When You'll need to reinstall the system (very seldom - only when You mess it up for good) Your files and configuration in \home will be intact.

---

### Post by Matt Houston on 2005-11-09
Excellent, thanks for the reply.

---

### Post by Matt Houston on 2005-11-14
OK, I couldn't be bothered when it came down to it, now I wish I had. Is there anything in Ubuntu like partition magic I could use to resize the parititons?

---

### Post by Pablo_Escobar on 2005-11-14
gparted I'd recommend :)

---

### Post by matthewv on 2005-11-14
If you're going to run gparted, just boot off the ubuntu live cd, which has it installed, and use it from there. It can't be run on mounted partitions (partitions in use)

---

