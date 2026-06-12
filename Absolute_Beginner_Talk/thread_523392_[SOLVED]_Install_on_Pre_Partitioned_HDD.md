---
title: "[SOLVED] Install on Pre Partitioned HDD"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Mukaeutsu on 2007-08-11
I have recently reformatted my computer, planning to install a Windows/Ubuntu DualBoot. I am new to linux but had played with the LiveCD and liked what i saw.

I have:
39gb(NTFS) With Windows XP installed
24gb(NTFS) for Documents and whatnot
16bg(RAW) prepared for my Ubuntu install

When i enter install, it gives 4 options (which i have here paraphrased by what i understood them as)
-Partition and install on empty
0%==========65%-----------100%
-Install on entire disk
-Install on empty
-Manual (which i explored in and located the RAW part, but felt uncomfortable)

I have tried to find forum/info to assist with this, but all either were irrelevent or the process did not seem to match up at all to what the installer was stepping me through.
I am almost entirely in the dark when it comes to some of the linux terminology, but am willing to learn, but couldnt fully understand WHAT exactly the installers options were.

Any and all assistance will be greatly appreciated,
Mukaeutsu

---

### Post by macogw on 2007-08-11
Use the "manual" one actually partition it again so you have about 1GB separate for swap.  the big chunk will have "use as" set for ext3 and the "mount point" should be /

---

### Post by Mukaeutsu on 2007-08-11
great thanks a ton macogw, ill try that right away
if i have any other questions, ill let everyone know
thanks

---

