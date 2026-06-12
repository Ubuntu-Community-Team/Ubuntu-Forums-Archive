---
title: "removing ubuntu"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by 613 on 2007-11-19
OK, here's the problem. I want to make the machine a dual boot but it already has 7.10 on it and won't allow an install of my win2000.Do I need to remove Ubuntu and install 2000 and then reinstall Ubuntu to get the dual boot? How is Ubuntu removed or is there an "F-Disk" feature I could use to do this.

Ric

---

### Post by LaRoza on 2007-11-19
To easily do this, you can use GParted to erase all partitions, then install Windows, then use GParted again to resize and create the appropriate partitions. Then install Ubuntu, which will add Windows to Grub.

Just delete or reformat the partition to get rid of Ubuntu. 

GParted is in the link in my sig.

---

### Post by jaybombalous on 2007-11-19
u remove ubuntu by booting to the liveCD and then running fdisk from the terminal.

Or you can run fdisk from within a windows boot. Either way u want to delete the partitions and restart from the beginning.

---

### Post by 613 on 2007-11-19
OK, I'm a dummy here, Is GParted part of the 7.10 distro? Do I need to go find it?

---

### Post by LaRoza on 2007-11-19
It is on the Ubuntu disk, but getting the GParted live cd is recommended. Look in the link in my sig.

---

