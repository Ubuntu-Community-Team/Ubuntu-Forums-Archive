---
title: "Removing partitions in a dual boot environment."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by TopHatCat on 2007-06-02
Heres the situation:

My laptop has a Windows XP partition, a couple of Ubuntu 7.04 partitions, and it HAD one 256-bit encrypted AES partition.

I wanted to reclaim the encrypted 10GB partition as part of my primary Windows XP partition using Partition Magic but it seems that I won't be able to do that unless I remove the Linux partitions and then resize the primary partition accordingly.

Since this computer is a dual-boot and it uses GRUB, would removing my Linux partitions (and GRUB as a result) cause my Windows partition to no longer be bootable?

I don't mind removing the Linux partitions and resizing my hard disk and then reinstalling Feisty again and reconfiguring it so long as it won't brick my computer in the process. :)

---

### Post by AtrejuT on 2007-06-02
Indeed if you remove the Ubuntu partition your computer will not be able to boot.
However if you just repartition and reinstall Ubuntu from the live CD right afterwards (after all you don't need to be able to boot for that) grub will be reinstalled as well and windows again be added to its list.

This - like all repartitioning stuff - is not without danger though. Take care and be careful which partitions you delete!

---

### Post by TopHatCat on 2007-06-02
Great, thanks for the advice!

<3 this community! :D

---

