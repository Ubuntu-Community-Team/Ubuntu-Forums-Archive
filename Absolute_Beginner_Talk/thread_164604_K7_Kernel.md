---
title: "K7 Kernel"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-04-23
I'm currently running Dapper Beta with 2.6.15-20-386

I have an AMD Athlon (XP) 3000+ overclocked to 3200+

I read somewhere that my system should run faster using a K7 kernel.

So 2 questions..

1. Is it ok to swap this in Dapper Beta without any issues?
2. Which one do I install, there seem to be a few K7 ones.

---

### Post by woedend on 2006-04-23
1)perfectly ok.  i doubt your system will run any faster, but might as well use it, i do.
2)just install the package linux-k7.  Its a metapackage that will automatically install the right latest k7 kernel, restricted modules for it, and better yet, automatically upgrade them when a new version comes out and you run an upgrade :).

---

### Post by _simon_ on 2006-04-23
Thank you for the quick reply.

I'm using the K7 kernel now :)

---

### Post by woedend on 2006-04-23
cool :) glad to be of help.  If you are very short on space, or just a neat freak, you can search for 2.6.15    in synaptic and remove anything that ends in 386 safely.  But it doesn't hurt anything being there, and in certain rare cases can save ya.

---

