---
title: "Partitioning an already partitioned drive"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by LIKMARK on 2007-04-21
Probably not the first one to ask this question, anyhow:

My 250 gb hdd is partitioned to c: 12,5 gb free and e: 150 gb free, can I partiton it once more for the ubuntu os?

Thanks!

---

### Post by overdrank on 2007-04-21
> **LIKMARK said:**
> Probably not the first one to ask this question, anyhow:

My 250 gb hdd is partitioned to c: 12,5 gb free and e: 150 gb free, can I partiton it once more for the ubuntu os?

Thanks!

Hi and welcome  yes you can partition it again and again. I have 4 partitions on my 160gb now. :guitar:

---

### Post by LIKMARK on 2007-04-21
I also heard something about linux overwriting the boot sector, but that it can be restored, what does this mean practically? problems booting or what?

---

### Post by rillip on 2007-04-21
You can repartition using the gparted utility in the installer to have up to four partitions.  You can use it to resize any of the partitions you have now and make new ones.

Edit:  In regards to your boot sector question.  You make it sound like Linux is breaking it, but it does not.    It does overwrite the master boot record to use Grub.  Grub will allow you to chose your OS.  It automatically detects both your Linux and Windows installations and allows them to run normally.  I haven't seen it with Vista per say, but it works fine with 95 - XP with the defaults.

---

### Post by LIKMARK on 2007-04-21
Allright! No worries then! Thanks

---

### Post by Patrick K on 2007-04-21
There is a 4 partition limit for primary partition but if one of those is an extended partition, you can have an unlimited number of partitions. An extended partition is like a container that can hold many partition called logical partitions. 

For example, I have two fixed disk. One has 9 partitions; one primary, one extended, and 7 logical partition (8 usable). The other has one primary, one ext, and 5 logical partitions for a total of 7 (6 usable). You can format an entire drive as an extended partition but some OS's will only boot from a primary partition. In practice you never see the extended partition no data is saved to it, only to the partitions contained in it.

---

### Post by trents on 2007-04-21
Note: You can have only four primary partitions on a disk that has an NTFS partition. However, you can make some of the partitions logical or extended partitions and so have more than four. Only some kinds of partitions can be logical, however, and the swap partition is one of them. Likmark, after linux is installed then you can edit the menu.lst file (sudo gedit /boot/grub/menu.lst) to move the Windows boot up info ahead of the linux kernels boot info so that your computer will boot into Windows by default. Otherwise, you will have to tab down through the kernel list at boot up to get to the Windows info if your want to boot into Windows.

Steve

---

