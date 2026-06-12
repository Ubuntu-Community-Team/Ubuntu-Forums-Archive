---
title: "libstdc++-libc6.2-2.so.3 for 64-bit Feisty"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ebeaty on 2007-04-12
I am trying to run an older 32-bit application on both the 32-bit and 64-bit Feisty Betas.  Each time I do, I get the message:

[FONT="System"]error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory[/FONT]

On my 32-bit Feisty, I was able to run 
[FONT="System"]sudo apt-get install libstdc++2.10-glibc2.2[/FONT]

and it fixed the problem.  But on 64-bit Feisty, I get:
[FONT="System"]E: Couldn't find package libstdc++2.10-glibc2.2[/FONT]

I already checked, and the universe and multiverse repositories are available.

Can anybody help?

---

### Post by ebeaty on 2007-04-13
Moving this question to the 64-bit forum.

---

