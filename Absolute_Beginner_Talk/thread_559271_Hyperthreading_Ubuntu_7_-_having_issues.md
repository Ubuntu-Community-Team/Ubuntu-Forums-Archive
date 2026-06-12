---
title: "Hyperthreading Ubuntu 7 - having issues"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by l1carter on 2007-09-25
Hello all,

I have recently installed Ubuntu 7 on my Dell XPS M170 which comes with a Pentium M 2.13GHz processor. When looking at "/proc/cpuinfo" it reports my CPU at 798.00MHz. 

After much online searching it looks like it is due to hyperthreading... so I then proceeded to edit my /boot/grub/menu.lst file to pass the kernel option "ht".... this for some reason it doesn't work after rebooting and my cpuinfo file still shows 798.00Mhz...

However, if I (first remove the ht option in menu.lst) then break the boot and edit "e" the kernel options there by adding "ht" it appears to work  for a few minutes after logging into to KDE then my cpu drops again (after about 5 minutes) to 798.00 (while the power supply is connected still...)

Has anyone seen this issue before? With hyperthreading shouldn't my cpu drop when power is dissconnected then raise when power is applied again?

Any advice would be appreciated.

Thanks in advance.

---

### Post by Kilz on 2007-09-25
> **l1carter said:**
> Hello all,

I have recently installed Ubuntu 7 on my Dell XPS M170 which comes with a Pentium M 2.13GHz processor. When looking at "/proc/cpuinfo" it reports my CPU at 798.00MHz. 

After much online searching it looks like it is due to hyperthreading... so I then proceeded to edit my /boot/grub/menu.lst file to pass the kernel option "ht".... this for some reason it doesn't work after rebooting and my cpuinfo file still shows 798.00Mhz...

However, if I (first remove the ht option in menu.lst) then break the boot and edit "e" the kernel options there by adding "ht" it appears to work  for a few minutes after logging into to KDE then my cpu drops again (after about 5 minutes) to 798.00 (while the power supply is connected still...)

Has anyone seen this issue before? With hyperthreading shouldn't my cpu drop when power is dissconnected then raise when power is applied again?

Any advice would be appreciated.

Thanks in advance.

This is normal activity on a laptop. When you are running off of the battery it slows things down to conserve power and give you longer time to use it on a battery charge. When its pluged into the wall and power is in huge supply it runs ar top speed. All operating systems do this, even windows.

---

### Post by mcduck on 2007-09-25
First, Hyperthreading has nothing to do with CPU speed. Hyperthreading means that the CPU reports it as 2 processors instead of one which in some cases makes balancing load between multiple running applications work better.

Your CPU speed is throttled based on CPU use, to always give you full performance when needed but at the same time reduce power usage (and heat & noise) when full CPU speed is not needed. Just run some program that uses a lot of CPU power and you'll see the speed jump up instantly.

---

### Post by hyper_ch on 2007-09-25
Just on a sidenote: There is no Ubuntu 7... there is Ubuntu 7.04  (--> Released in April (=**04**) 200**7**) with the code name "Feisty Fawn".

The next release will be Ubuntu 7.10 which will be released in October with the code name "Gutsy Gibbon".

So Ubuntu 7 could be referring to either one ;)

---

