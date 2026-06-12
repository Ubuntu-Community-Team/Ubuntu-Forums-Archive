---
title: "Newbie needs help installing ubuntu"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by gslavik on 2006-10-12
im new to linux but i have decided to ditch xp and switch to ubuntu well durring the first boot of the cd right after mounting the file system the screen goes black and says loading kernel i have tried everything i know to fix this problem

Pentium d 3.4
Ga-965p-ds3 mobo
msi nvidia 7000 pcie
2 gigs ddr2 corsair ram
2 wd 160 gig sata2 hd strip0 (yes i have tried diching the raid)

any help would be greatly appreciated

---

### Post by pay on 2006-10-12
I found that problem with my nforce 4 board with the amd64 installation, but the 32bit iso worked. That's what made me ditch Ubuntu and use Gentoo.

---

### Post by encompass on 2006-10-12
That was not a very helpful remark, not like gentoo would be much better.
Have you tried the safe graphics boot?
You could also try to work with the alternative cd and install in text mode.

---

### Post by gslavik on 2006-10-12
i have tried safe mode but it still does the same thing
is there some issue with my chipset i am having problems with suse droping my dvd just after install starts

---

### Post by taurus on 2006-10-12
Have you tried using the alternate CD?

---

### Post by tommcd on 2006-10-12
I think there is a problem with the ICH8 southbridge chipset not being supported by the kernel yet. Do a search for ICH8 in the forums:
[http://ubuntuforums.org/showthread.php?t=234706&highlight=ICH8](http://ubuntuforums.org/showthread.php?t=234706&highlight=ICH8)
[http://ubuntuforums.org/showthread.php?t=270852&highlight=ICH8](http://ubuntuforums.org/showthread.php?t=270852&highlight=ICH8)
[http://ubuntuforums.org/showthread.php?t=256922&highlight=ICH8](http://ubuntuforums.org/showthread.php?t=256922&highlight=ICH8)
I don't know if there is a way around this. Hopefully, it will be supported in Edgy.

---

