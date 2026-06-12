---
title: "Restoring The HDD to a Single Partitian"
date: 2007-06-23
forum: Apple Intel Users
---

### Post by Luigi239 on 2007-06-23
Hello everybody. I am trying to restore my Macbooks HDD to a single partition, because I am running out of space on the OS X side of things. How would I do this using using the Live CD and Gpart?

Thanks.

---

### Post by ivesjd on 2007-06-23
IFRC, you cant "grow" hfs+ partitons with gparted. You can only shrink it. You can either do it from terminal or use something like iPartition on the OS X side. One thing you could do to, is delete the extra lanuges and stuff in OS X, monolingual will give you 1gb or more, and then Microsoft Office has 1-2gbs in foreign dictionaries.

---

### Post by thully on 2007-06-23
If you just have two partitions (1 OS X + 1 Ubuntu), simply run Boot Camp Assistant in OS X and tell it to restore to a single partition.

If you have 3 or more partitions (i.e. OSX+Ubuntu+swap), just run through the Ubuntu install again, deleting the Ubuntu partitions and creating a single Ubuntu partition to install on.  Then, let the install run for a while (at least to the point which it starts copying files) and reboot into OS X.  Boot Camp Assistant will then let you restore to a single partition.

Gparted will probably work in the second case, but I'm not sure if the Feisty version is GPT-aware and able to resize OS X partitions without borking your install up.

In any case, you may want to try Ubuntu in VMware Fusion, Parallels, or another VM like VirtualBox on OS X - it works pretty well save for 3D if you have enough RAM (at least 1GB). I'm personally waffling between doing a VM and a separate partition on my MacBook for this very reason (I only have a 60GB drive)

---

### Post by ivesjd on 2007-06-23
Oh ya, I forgot about the bootcamp work around. You can boot to the ubuntu live-cd, run gparted and make the swap and ubuntu partitions one part. and then run bootcamp.

---

