---
title: "What is the diff between 386 &amp; 686 kernels?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by Psquared on 2005-10-09
When should I use the 686 instead of the 386? I have a Pent Centrino 1.6 laptop. Are there any advantages to one over the other for me?

---

### Post by jasmuz on 2005-10-09
The differences are some memory optimizations made for the i686 kernel. In theory it should work your processor less than the i386 kernel with the same logical results.

---

### Post by Psquared on 2005-10-10
[QUOTE=jasmuz]The differences are some memory optimizations made for the i686 kernel. In theory it should work your processor less than the i386 kernel with the same logical results.[/QUOTE]

So the i386 is made for older computers and the i686 should work better on most newer Pentium IV's ??

---

### Post by patrick295767 on 2005-10-10
[QUOTE=Psquared]So the i386 is made for older computers and the i686 should work better on most newer Pentium IV's ??[/QUOTE]

rpm for mandrake are always with i686 ?

why do the i386 are always for debian : dpkg -i ... ?

Thank you for ur information

---

### Post by jeffjj on 2005-10-10
I do not know the technical reason but I had to use the i686 to recognize all my memory. The i386 can only read up to 768M (give or take a little) , but I have a 1.2 G on my machine. I found that out in these forums and switched with no problems. I also saw another posting that you are supposed to use whichever one you want without any problems. Both are officiall supported.

---

### Post by Kyral on 2005-10-10
In case you are wondering, the i386 kernel is default because it WILL work on ANY x86 based machine. That being said, the i686 (for P4s) and K7 (for Athlon XPs) is slightly better, if not just because it sees higher amounts of memory without a recompile

---

### Post by mlomker on 2005-10-10
> i686 (for P4s) and K7 (for Athlon XPs)

It actually supports any Pentium (from the old Pro's on up).  The memory is the big thing--the i386 kernel has a 1 Gig total limit (you'll actually get a smaller number because video roms and other things take some RAM).  The other kernels have a 4 Gig limit (once again, minus a bit for roms).

---

### Post by Kyral on 2005-10-10
Ooops. Oh well I run an Athlon XP ;P

---

