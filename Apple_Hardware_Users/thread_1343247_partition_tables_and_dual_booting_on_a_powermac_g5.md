---
title: "partition tables and dual booting on a powermac g5"
date: 2009-12-01
forum: Apple Hardware Users
---

### Post by hydraulicjj on 2009-12-01
Hi
I recently bought a powermac g5 and a 1TB hard drive to put in it. What i want to know is wether or not it is possible to use the GUID partition table to dualboot mac osx and ubuntu karmic ppc on a powermac g5 dual 2.0GHz and if not would it be possible to install ubuntu on a Apple Partition Map drive after installing mac osx?

---

### Post by tiresia on 2009-12-01
An Apple PowerPC uses the 'apple partition map'. Anyway you can dualboot without problems. There are plenty of howto on this forum about it. 
The easiest way:
1. Boot from the MacOSX installer and make two partitions (hfs+), installing MacOSX on the last partition.
2. Boot from the Ubuntu installer and delete the first partition. Leave the installer to partition the free space as needed (it will create by default 4 partitions).

If you want to install Ubuntu 9.10 and you want to use the Desktop CD, be aware that it is oversized, and therefore you should use a DVD or follow a thread on this forum to overburn a CD.

For more infos on powerpc booting process, you may want to read this thread [PPC - Yaboot - How to configure the PPC Bootloader - Multibooting]("http://ubuntuforums.org/showthread.php?t=994882")

---

### Post by hydraulicjj on 2009-12-01
> **tiresia said:**
> An Apple PowerPC uses the 'apple partition map'. Anyway you can dualboot without problems. There are plenty of howto on this forum about it. 
The easiest way:
1. Boot from the MacOSX installer and make two partitions (hfs+), installing MacOSX on the last partition.
2. Boot from the Ubuntu installer and delete the first partition. Leave the installer to partition the free space as needed (it will create by default 4 partitions).

If you want to install Ubuntu 9.10 and you want to use the Desktop CD, be aware that it is oversized, and therefore you should use a DVD or follow a thread on this forum to overburn a CD.

For more infos on powerpc booting process, you may want to read this thread [PPC - Yaboot - How to configure the PPC Bootloader - Multibooting]("http://ubuntuforums.org/showthread.php?t=994882")

Cool thanks for the quick reply. I take it then that i cant use the guid partitioning scheme? also is it possible to have ubuntu on the second partition instead of the first? thanks again

---

### Post by tiresia on 2009-12-01
> **hydraulicjj said:**
> Cool thanks for the quick reply. I take it then that i cant use the guid partitioning scheme? also is it possible to have ubuntu on the second partition instead of the first? thanks again

Sorry, but why you want to use a guid :o
Yes, you can have ubuntu on the second partition, but unless you do a manual partitioning, for that you need a bit more experience or patience to learn, you will get a bit strange (but still working) situation

_Example_ Let's say you install Mac OSX on /dev/sda1, and then you let the installer partitioning automatically for you, you will get following situation:
/dev/sda1 MacOSX
/dev/sda2 Apple Partition Map
/dev/sda3 Apple Bootstrap
/dev/sda4 Ubuntu
/dev/sda5 Swap

It means that the installer will create the partition map not at the beginning of the hd. As I said, it will work anyway, it is just unusual.

Actually there is another reason to avoid such a situation, but it shouldn't be your problem. The reason is that, Open Firmware (ppc-bios) if reset, tries to boot from the first bootable partition. It means that you wouldn't see the Bootloader anymore (unless you press the opt-key at boot up)

---

### Post by hydraulicjj on 2009-12-01
Cool thanks once again i think ill probably just reformat my whole drive again as its gonna be a lot easier and the openbios problem would probably get annoying (i have to reset things like that quite often:D) Thanks again.

---

