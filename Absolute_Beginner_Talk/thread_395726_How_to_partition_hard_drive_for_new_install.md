---
title: "How to partition hard drive for new install"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by mirrrad on 2007-03-28
I am planning to install Ubuntu 6.10 on a machine which already has Windows XP installed. There are currently two partitions on the system, a 20Gb one which has my Windows installation, and a 90GB one which has 75Gb data and 15 Gb free space.

I want to make this 15Gb free space into a new partition, and install linux on it, without losing any data currently on my hard disk. And I also want my machine to be a dual boot system.

Could someone please tell me the steps I should follow to do the same. Also, please tell me if what I am planning to do is the good thing to do or should I make more than one partition to install linux (a separate home partition or anything of that sort?)

---

### Post by ziggykg on 2007-03-28
Ubuntu can pick up the free space and use it without touching the other partitions.  Grub (the bootloader) will recognise the existing Windows installation and set up the bootloader so you can dual boot.

Just as a side note, I had 10gb freespace on a hard drive with XP on it.  Using a Feisty beta CD, I went from 0 to dual booting XP and Linux in about 20 mins with minimal fuss.  Ubuntu rocks!! :guitar:

---

### Post by GMachine_24 on 2007-03-28
Hi:

What you want to do is very easy if you have any experience with computers.

The Ubuntu install disk will ask you what you want to do - use all the space on the hard drive, use the free space to install Ubuntu partitions, etc. You can allow the computer to automatically set up the three partitions usually used in an Ubuntu system (there is more information on these if you want e.g. ext3 etc.).

Basically, if you don't tell the install program to erase or use your entire hard disk, you will be ok. I'm not sure if there is an option that says "I want to set up a dual-boot computer" but Ubuntu will install its software without touching the Windows partitions and when you reboot, voile, you will have a dual boot system.

Yes, it's that easy.

Good luck.

GM

---

