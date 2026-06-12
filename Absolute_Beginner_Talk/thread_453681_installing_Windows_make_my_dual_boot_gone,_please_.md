---
title: "installing Windows make my dual boot gone, please help"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-24
Hi
thank you for reading my post.
one week of my effort is likely to be gone.

I had Ubuntu and windows XP working file (dual boot on two sata hard disks)
my windows XP got currupted and i tried to fix it (reinstall it) now after windows installation is finished, my dual boot screen is not showing anymore and computer directly goes to windows


can some one please tell me how i can bring back my dual boot?

I have well configured my linux and can not afford to lose it :-(


Thanks

---

### Post by yacinux on 2007-05-24
if u can,  try to install  windows  first then Ubuntu.;)
or use Ultimate boot  CD:D

---

### Post by Sparkster185 on 2007-05-24
I'm guessing Windows overwrote the partition that contains (contained) the GRUB or LILO bootloader, and replaced it with it's own boot loader.

The Ultimate Boot CD should be able to fix that for you.

---

### Post by lazyart on 2007-05-24
Your grub got hosed by Windows.  There are a hundred posts here on how to reinstall Grub.

---

### Post by legolas_w on 2007-05-24
Hi
I do not have Ultimate boot CD, I have Ubuntu 7.04 DVD, I tried and boot the system with that DVD and it just showd something similar to first day installation.

it does not boot into my already installed linux, what should i do now?


thanks

---

### Post by gn2 on 2007-05-24
This may help: [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by hakimaki on 2007-05-24
There are wonderful Grub boot disks available out there for download.  I forget the name (perhaps SuperGrub--dont quote me however) but you can easily find one for download in under 5 minutes of googlin' or torrent search.  It has worked wonders for me and it was so easy, even a caveman could do it.

---

### Post by indytim on 2007-05-24
Super Grub is here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

p.s.  Herman's reconfiguring his site so old bookmarks may not work...had to "Google" to find the link above.

IndyTim

---

### Post by Clay_Banger on 2007-05-24
> **gn2 said:**
> This may help: [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)
That is what you need. Follow that tutorial and it will be all good. I had a similar problem after reinstalling windows, and that fixed it for me.

---

