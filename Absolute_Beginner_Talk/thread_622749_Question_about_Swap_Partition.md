---
title: "Question about Swap Partition"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-25
I want to install Ubuntu again in a partition beside Vista if I assign a drive for Ubuntu will it create the swap partition or I have to do it manually if so can I make logical partition  or it has to be primary.

The reason I am asking I installed Vista,Fedora.and Ubuntu plus the swap that is four primary the rest of the drive is a waste I can't do anything with it because I can't have more than four. 
THANKS

---

### Post by staticvoid on 2007-11-25
if you set up the partitions manually upon install you probably will need to also create a swap partition. so you have grub, restore, vista, fedora, swap, unallocated space?

sv

---

### Post by shoaibi on 2007-11-25
i think if you use the guided partition it creates itself, else in manual like you are doing, it will ask you to create a swap drive. 
Swap drive can been logical, only the /boot needs to be primary, though making swap a logical might effect performance,

---

### Post by indytim on 2007-11-25
You only need one /swap partition... period.  With your other ops, you have swap already installed.  Just identify an existing swap at time of install (will probably use the manual configure route).

IndyTim

---

### Post by mahiyar on 2007-11-25
You cannot have more than four primary partition but you can have as many extended partitions within a logical partition that you want, and unlike windows linux can be installed in any partition type. If you are using fedora you must have a swap partition made for fedora the same can make do for Ubuntu, no need to make a seperate swap for Ubuntu.

---

### Post by jmfa59 on 2007-11-25
With this kind of response in Ubuntu forum who needs fedora.

---

