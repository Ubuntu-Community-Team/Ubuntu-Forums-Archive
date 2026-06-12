---
title: "beginner with kernel panic! help!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by whoKnew on 2007-04-20
hey everyone.
hopefully someone can point me in the right direction...

i've tried to install/run ubuntu from the boot cd on a recently-acquired old ibm thinkpad 600e (pII, 363 mHz, 224 mb ram). as an anecdote, it has win xp loaded and runs perfectly.

after i get to the boot menu and try to run ubuntu, i get the following error messages:

[167.208888] invalid compression format (err=2)
[167.215016] kernel panic - not syncing: VFS: unable to mount root fs on unknown - block (1,0)
[167.215094]

my problem, besides this, is that i'm absolutely new to linux and have little programming abilities. 
i have no idea what could be causing this or where to start trying to solve the problem. i've found some forum posts for non-ubuntu distributions concerning similar error messages, but most of the solutions all involve some sort of command line to enter within linux. i don't have this option, as the kernel can't load and i have to reboot to the same problem.

i've tried two different iso images (of the same version) and they both give me the same error message.

any thoughts?

thanks so much in advance.
:: i

---

### Post by oilchangeguy on 2007-04-20
on that machine you'll probably need to use xubuntu. it's designed for lower powered machines, like yours. ubuntu needs at least 256mb of ram. xubuntu needs (i think) at least 128.

---

### Post by steve.horsley on 2007-04-20
It sounds as though the installer CD may be corrupt - you could try re-burning at as low a speed as you can. 

oilchangeguy may be right about the memory too. In which case, the "alternate" installer CD will have a much better chance of success.

---

