---
title: "Kernel won't install"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by 4th guy on 2007-02-11
I got the alternate cd of the Ubuntu 6.1 (as the live cd won't work because of the ATI video card).
The install goes fine up to the point where I am requested to select a kernel. The problem is that all the available kernels don't install and result in a broken installation no matter what I select. Are there any installation instructions available that I might have skipped by mistake?
This is how I set up my hard disks:
---
HDD1: Partition 1: NTFS (Windows)
HDD1: Partition 2: EXT3 (boot [GRUB])
HDD1: Partition 3: NTFS (user files for Windows)
---
HDD2: Partition 1: EXT3 (root)
HDD2: Partition 2: EXT3 (home)
HDD2: Partition 3: SWAP
---
Thanks in advance for any help you might offer.

---

### Post by jvc26 on 2007-02-11
Why does it ask you to select a kernel? I have never been asked to select one from the alternate install cd - have you checked the .iso for md5 to make sure that its correct and checked for a burn error as I have never been asked to select a kernel during 6.10 alternate install.
Il

---

### Post by mikewhatever on 2007-02-11
[Herman's Site]("http://users.bigpond.net.au/hermanzone/") has very good instructions for Alternate installer. It deals with Ubuntu/Windows on one HD, and I can see you have two, so disregard whatever it says about windows. I've also used the Alternate installer, but do not remember having to choose the kernel. It is supposed to be loaded according to the hardware detected on the PC.

---

### Post by 4th guy on 2007-02-23
I still didn't manage to install it, but I did save the installation logs. Anyone who wants to take a peek can find them [here]("http://www.geocities.com/ivanxuereb/install.zip").

---

