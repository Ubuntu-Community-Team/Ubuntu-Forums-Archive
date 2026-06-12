---
title: "GRUB problem"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by JaskulaR on 2007-02-22
Hey guys, 

I just bought a Toshiba A135-S4407 preloaded with Windows Vista Home Premium. It's neither my first Vista machine nor my first time installing Linux (I had Fedora Core on my old laptop). 

I've never had a dualbooting problem until today. 

After wrestling with Installing Ubuntu (and getting it done), and after fiddling with it trying to get my WiFi to work (a problem for another day) I tried to restart my machine and go into vista. The problem is with the GRUB loader. 

When I hit escape to go into the load screen, I have three options, load ubuntu, load it in recovery mode, and system test. There is no option for me to load Vista. I know I partitioned and such my harddrive correctly as the Ubuntu partition size is all how it should be (and again, I did do this once before with no issues). I'm really kind of stumped. Any help would be appreciated.

---

### Post by matt271 on 2007-02-22
boot off an old win98 boot disk. open fdisk and u can change the active partition. change it to your windows 1 to boot off windows, and change it to partition linux is on to boot into linux. u might have to run fdisk /mbr to get rid of grub if it keeps causing problems.

---

