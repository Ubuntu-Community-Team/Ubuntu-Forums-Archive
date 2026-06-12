---
title: "Installation of 5.10 freezing"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-05-01
I am trying to install ubuntu 5.10 on a computer I recently built.  It has an AMD 64 precessor and so I am using a 64 edition install disc.  Everything was going swimmingly until it got to "Installing GRUB boot loader."  The display says 0% (and it has for about four hours).  At the bottom it says installing the 'grub' package. . .
Everything else was going so well and I am very confused as to why the install process has suddenly stopped.

---

### Post by daWabbit on 2006-05-02
How are you partitioning the drive? Are you letting the installer do it or did you do it manually. I have only done a few AMD 64 installations, but one of them would not install GRUB. That installation was simply an adequate swap partition and a / partition. I repartitioned so that hda1 was a 20 MB partition mounted on /boot, then hda2 was / and hda3 as swap. 

I believe, on very little evidence, meaning I could well be wrong, that GRUB wants a certain minimum size for /boot and is happiest if it is a separate partition. Setting the size around 20 MB ensures this and leaves room for updated kernels that might come along. This has worked for me in the only time I have encountered the problem. Thanks to RayF for suggesting it.

Jack

---

### Post by abbrew on 2006-05-02
That sounds great, but I am really a beginner.  Would you mind explainging how to partition the HD in the way you suggested?  I am currently at the Partition Disks step on the install.  Please keep it as simple as possible if you can.  Sorry I am so new to this subject and require extra clarification.  I really appreciate your help.

Alex

---

### Post by nanotube on 2006-05-02
simplest way is to just point it at some empty space on the disk (without any partitions on it), and tell it to automatically partition the space.

---

### Post by abbrew on 2006-05-02
I tried, to the best of my abilities, to do what you have told me to do, but I must have done something wrong because the installation still stops at the grub install phase.

---

