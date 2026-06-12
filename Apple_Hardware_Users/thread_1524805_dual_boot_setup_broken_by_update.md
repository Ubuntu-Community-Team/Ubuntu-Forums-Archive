---
title: "dual boot setup broken by update"
date: 2010-07-05
forum: Apple Hardware Users
---

### Post by nourathar on 2010-07-05
I installed Ubuntu 10.04 lucid lynx 64bit on my mac pro in a dual boot setup with os x. When installing I had some trouble figuring out the partitions, especially because the thing happened with the [extra partition from nowhere]("http://ubuntuforums.org/showthread.php?t=1297229"). I deleted the small partition created by the installer, synced the GPT and MBR, installed GRUB on /dev/sda4 and all was fine.

After my first software update my system is now broken, after rEFIt it got stuck on a black screen. I started up from the livecd, chrooted into my system, reinstalled GRUB on /dev/sda4, installed it on /dev/sda too, but that did not really help. I now get to the GRUB rescue shell, but I'm pretty clueless what to do. Also it does not seem a widespread problem, since I didn;t find many reports of dual-boot macintels breaking with this update.
What can I do to restore my linux system ?

any insights very welcome...

J.

---

### Post by nourathar on 2010-07-06
Trying some more things in order to find a solution, or rather to localize the problem. Looking a bit in the dark, being the newbie I am...
Anyway I tried running grub-mkconfig (again), and looking at the file it produced it seems as if I have two kernels, I have 2.6.32-23 and 2.6.32-21. Can it be that something went wrong during my software update and that that left me with an inconsistent system ? What can I do to repair this ?

thanks for any insight or idea or suggestion what to check.. I'm considering to reinstall Ubuntu, which would be annoying because I would lose some stuff (but not much), but mostly I'm abit concerned that if I reinstall I might enounter the same problem at some point if I do not know better what is going on..
ciao,

J.

---

### Post by nourathar on 2010-07-06
ok, solved whatever it was by running sudo update-grub , hope I will understand what i'm doing at some point, I start to like Linux but after a week there is still a lot of fingers crossing and other voodo involved..

---

### Post by nourathar on 2010-07-13
ok, counter to a lot of advice I found on-line, I installed GRUB2 in the boot-partition of my disk, and since then all is very stable..
(Don't seem to find a way to delete this thread, since I'm not sure what this contributes to the online knowledge base...)

---

