---
title: "Change operating system disk"
date: 2013-11-23
forum: Any Other OS
---

### Post by tashimee2 on 2013-11-23
I have a dual boot system with Ubuntu 12.04 and Win XP. Win XP is on a IDE drive. What I would like to do is load Win 7 on a SATA drive, to replace Win XP. How do I change the boot menu to list Win 7 and take out Win XP?

---

### Post by oldos2er on 2013-11-23
Since your question has more to do with Windows than Ubuntu, I've moved it to Other OS/Distro Support.

---

### Post by mips on 2013-11-24
On which drive is grub installed?

You could simply reinstall grub or update it or use grub customiser.

---

### Post by tashimee2 on 2013-11-24
msdos is sda1. Windows is sda5. Ubuntu is sdc1. Thank you for your answer, I think I can take it from here. I think you are wrong, this is about the the grub loader, not windows. According to grub customiser it auto :popcorn:looks for other operating systems, so I don't have to worry about changing operating systems.

---

### Post by mastablasta on 2013-11-25
that or boot repair tool:[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2013-11-25
It may depend on which drive grub is installed into and that drive is the BIOS default. If sdc then you really do not need to do anything except.
sudo update-grub

But if grub is in the MBR of the IDE drive, removing it will prevent you from booting. Then you need Boot-Repair or a live installer to install grub correctly.
If you do not have grub in sdc you can easily install it when booted into the install in sdc.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdc but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck /dev/sdc
sudo update-grub

Before installing Windows be sure to set BIOS to boot from drive you are installing into first. Windows will install its hidden 100MB boot partition into the default boot drive. If that is sdc, it will corrupt Ubuntu as it does not see Linux partitions and will just stuff in a new 100MB partition overwriting whatever you have there. Many suggest disconnecting other drives to avoid issues.

      
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

