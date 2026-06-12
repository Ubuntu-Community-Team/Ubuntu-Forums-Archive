---
title: "Grub error 15"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by cinaibur on 2008-01-03
Hey guys. I just installed Ubuntu 7.10 on my second hard drive just to see what it's all about. I messed around on it for a little while and wanted to switch back into Windows on my other hard drive to play some games, but my computer won't start. It keeps getting stuck in the BIOS. I try to open my Windows hard drive and it starts using GRUB and the it says Error 15. What is going on? Did I mess up my computer? I'm sorry if this is a dumb question but I'm freaking out cause this is my only computer and now I can't use it.

---

### Post by indytim on 2008-01-03
1.  Checkout :[http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors")
2.  Backup then edit your /boot/grub/menu.lst file to find the offending entry.

IndyTim

---

### Post by chanhdat on 2008-01-03
OR, if you don't have anything important on Linux drive. delete that partition. Then, install Ubuntu again. That will overwrite the old GRUB, and you will have your computer as before. Caution; use this way too much will make your HDD die soon.....

---

### Post by indytim on 2008-01-03
> 
Caution; use this way too much will make your HDD die soon.....


Where did this tidbit come from?

---

