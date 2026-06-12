---
title: "GRUB Problems"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by ces1939 on 2007-10-10
:popcorn: Hi again!
I knew I would have to come back.
Here is my problem:
I have Win XP on 80 Gb SATA
PCLOS on 250 Gb SATA
I started to install Ubuntu CE on the 250, but did not know how to partition.
I chose instead to put it on 40 Gb IDE.
Everything went fine until I tried to boot XP and PCLOS from the splash.
It said that was an invalid option.
How do I set the GRUB to the XP drive? 
Or, how do I get the XP and PCLOS options to work?
Remember I am a noooooobe, need simple instructions.
Thanks in advance for any assistance.
Possibly, could it be easier to re-partition the 250 and if so, how?
Plus any instructions on avoiding the same problem in such a case.
ces1939

---

### Post by Pumalite on 2007-10-10
The mix of IDE and SATA drives is always a problem, but we might be able to solve it. Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by ces1939 on 2007-10-10
Units = sectors of 1 * 512 = 512 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63    16370234     8185086   83  Linux

/dev/sda2        16370235   488392064   236010915    5  Extended

/dev/sda5        16370298    24547319     4088511   82  Linux swap / Solaris

/dev/sda6        24547383   488392064   231922341   83  Linux



Disk /dev/sdb: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors

Units = sectors of 1 * 512 = 512 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *          63   156280319    78140128+   7  HPFS/NTFS



Disk /dev/hdc: 40.0 GB, 40020664320 bytes

255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors

Units = sectors of 1 * 512 = 512 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hdc1   *          63    74862899    37431418+  83  Linux

/dev/hdc2        74862900    78156224     1646662+   5  Extended

/dev/hdc5        74862963    78156224     1646631   82  Linux swap / Solaris


# This entry automatically added by the Debian installer for an existing

# linux installation on /dev/sda1.

title           failsafe (on /dev/sda1)

root            (hd1,0)

kernel          /boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda1 failsafe acpi=on resume=/dev/sda5 

initrd          (hd1,0)/boot/initrd.img

savedefault

boot





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sdb1

title           Microsoft Windows XP Home Edition

root            (hd2,0)

savedefault

makeactive

map             (hd0) (hd2)

map             (hd2) (hd0)

chainloader     +1


Is this right?
If I got it wrong, I will try again.
ces1939

---

### Post by Pumalite on 2007-10-11
Linux: (hd0,0)
Windows: (hd1,0)

---

### Post by ces1939 on 2007-10-11
How and where do I get those commands entered?

---

### Post by ces1939 on 2007-10-11
I decided to leave all the headaches and just remove Ubuntu from the IDE drive, reset the MBR on my Win XP, and stick with PCLOS on the other SATA.

---

