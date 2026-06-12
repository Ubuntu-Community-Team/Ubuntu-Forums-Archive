---
title: "Dual boot XP and Ubuntu"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by goMON on 2008-01-15
This has probably been answered many times, and i have used the Search, but i don't understand many of the posts, and what i want is a little different.

I have Ubuntu installed already, and that's the only OS installed, but how would i set up a Dual Boot with XP, without uninstalling Ubuntu first?

---

### Post by KhaaL on 2008-01-15
You'll lose your current MBR if you install windows, however the partition itself will be intact. GRUB can be reinstalled with [SuperGrub]("http://supergrub.forjamari.linex.org/?section=download")

Hope it helps :)

---

### Post by goMON on 2008-01-15
Thanks for the quick reply, but, whats that mean? :P
Whats MBR and whats GRUB?

---

### Post by skullmunky on 2008-01-15
MBR = master boot record.  It's a configuration on the hard drive (lower-level than the windows or linux operating system, file systems, partitions, etc) that determines which partition to boot from.

GRUB is the OS chooser screen that comes up when you boot ubuntu.  stands for Grand Unified Bootloader.  the boot process on, say, a linux+xp system looks like this

MBR loads GRUB
in GRUB you choose Windows or Ubuntu
if you chose Windows, GRUB boots the Windows partition
if you chose Ubuntu, GRUB boots the Ubuntu partition

When you install Windows, it doesn't think about the possibility that you might want other OS's on your drive.  So, it just sets the MBR to boot Windows.  This means your Linux partition will still be there, but you can't boot it.

SuperGrub is a little utility to fix this.

---

### Post by goMON on 2008-01-15
Ah thank you!
Do i install this SuperGrub on Ubuntu before XP Install or on XP after XP install?

---

