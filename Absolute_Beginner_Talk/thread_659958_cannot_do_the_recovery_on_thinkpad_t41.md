---
title: "cannot do the recovery on thinkpad t41"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by ldkha1979 on 2008-01-06
hi all,
I'm newbie with linux. I installed Ubuntu 7.10 on my T41 laptop. I think I still have the IBM recovery partition. Now I need to sell it to buy a new one, so I need to restore the WINXP. The problem is I cannot use the access IBM button to access to IBM recovery partition as before. Any suggestion?
Thank you very much!
Kha

---

### Post by Daveth on 2008-01-06
what does

```
sudo fdisk -l
```

throw up in a terminal? It will tell us what partitions are still present on your hard drive. Did you re-partition when you installed ubuntu in the first place?

---

### Post by (((X))) on 2008-01-06
boot from xp recovery cd to recover..
or xp installetioncd, enter recovery mode, execute FIXMBR..I think is better option.

---

### Post by ldkha1979 on 2008-01-06
> **Daveth said:**
> what does

```
sudo fdisk -l
```

throw up in a terminal? It will tell us what partitions are still present on your hard drive. Did you re-partition when you installed ubuntu in the first place?

Here is the output. I guess the recovery partition is Compaq diagnostics.

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4250    34138093+  83  Linux
/dev/sda2   *        4271        4864     4770360   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda4            4251        4270      160650    5  Extended
/dev/sda5            4251        4270      160618+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Daveth on 2008-01-08
yes, it looks like it is still there on sda2. However, the previous poster had the slickest solution which is to install the XP cd and start over- assuming they were gracious enough to give you one.

Or does XP all lie on sda2, with no cd available ?

I'm not really up on recovery partitions, so perhaps someone can say if it can be got at through GRUB - is sda2 bootable as such????

---

