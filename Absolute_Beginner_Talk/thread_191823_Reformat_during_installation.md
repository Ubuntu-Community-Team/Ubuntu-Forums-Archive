---
title: "Reformat during installation"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-06-08
Hi

I'm planning to overlay an existing suse 9.1 installation with 6.06, creating a /home partition. I'll have three linux partitions /, /home and swap. Do they have to be reformated? I suspect that I migth as well click the reformated box for all the partitions - I can't see it will do any harm, maybe just take a little longer - but I don't want to leave anything to chance.

All advice much appreciated.

Roger D

---

### Post by _simon_ on 2006-06-08
tick that reformat box! :)

"reformatting" doesn't take long at all.

---

### Post by r3st on 2006-06-08
swap doesnt no good. it just slows down you system.  DO NOT USE SWAP.

---

### Post by RogerD on 2006-06-08
Many thanks - I'll go with the reformatting.

---

### Post by bruce89 on 2006-06-08
[QUOTE=r3st]swap doesnt no good. it just slows down you system.  DO NOT USE SWAP.[/QUOTE]
You have to have at least 256MiB (for the expresso installer anyway).  My brother recommends 256MiB for desktops.  Why would swap slow the computer down, it would only if it was being used, I thought.

---

### Post by catlett on 2006-06-09
Swap is virtual memory. It is only used when your compouters ram resources are used up. If you have enough ram to run your applications then swap is not used.
If you run a resource heavy appllication and you use up all the available ram  the computer uses part of your hard drive (your swap partition) to create virtual memory. The computer will run slower on "hard drive virtual memory" than from ram but that is not swap slowing down your computer. It is the result of your using up all your ram and the system having to use part of your hard drive. The virtual memory is going to be less responsive than ram but if you didn't have it your computer would really slow down because it wouldn't even have that resource when it's ram ran out.
Make a swap just in case you need it. If you don't run out if ram, it isn't used. It doesn't slow down you computer.


P.S. Another way to explain it. The swap aprtition is the same thing as a swap file in windows, except in linux a partition is used and in windows a file is used. A swap file doesn't slow down windows and a swap partition doesn't slow down linux. It is a needed resource if you run a low ram system.

---

