---
title: "Installing Ubuntu on 2nd hard drive"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by mit on 2006-09-04
I have Ubuntu installed on my laptop, and now would like to add it to a second physical drive on my desktop system. The desktop currently has XP Pro installed on it and is almost full of things I need.

The problem i see, is that although you can swop the boot order in the BIOS, normally you have an option of floppy, CD, Network or IDE. 
I was thinking of swopping the boot order if i wanted to boot in to XP from the BIOS if there were an option of say IDE 0 and IDE 1.
Am i thinking along the right lines, or is there a better way of doing it?

Mit

---

### Post by comppsyco on 2006-09-04
Actually, Ubuntu will install what's called a "boot loader." After the bios is done, the boot loader will launch and ask you whether to boot into XP or Ubuntu. This should happen relitavely automatically. You shouldn't need to change the boot order at all.

---

### Post by mit on 2006-09-04
Excellent! How does this work? 
I take it Ubuntu detects the other drive somehow and that there is an Operating System on it?

Mit

---

### Post by comppsyco on 2006-09-04
Yes. During the install process. I've got to go, so I can't expain more, but it should be pretty easy. All you have to do is make sure you don't choose to install to a partition that has XP on it.

---

### Post by mit on 2006-09-04
oh, great, thanks. :KS 

mit

---

