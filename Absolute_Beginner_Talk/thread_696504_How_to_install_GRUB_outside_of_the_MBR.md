---
title: "How to install GRUB outside of the MBR?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Phantomdagger on 2008-02-14
What do I have to do if I want to place GRUB on the partiton I have for Ubuntu, which, according to the installer, is partition 6?

Do I type in (hd0,2), since the Ubuntu partition is technically the third partition I created, (hd0,6), or, what? Kinda lost here.

---

### Post by oedha on 2008-02-14
i am not really get your point......but
GRUB will automatically installed to MBR doesnt matter which partition you used.

---

### Post by mister_pink on 2008-02-14
Grub just counts from the first partion being 0, in order along the disk. So 6 is unlikely, do an 
"sudo fdisk -l" to find out what partions there are, and count up from the bottom (or top, as the case actually is).

---

### Post by logos34 on 2008-02-14
> **mister_pink said:**
> Grub just counts from the first partion being 0, in order along the disk. So 6 is unlikely...

mister_pink,
It makes sense if the partition is a logical.  You might want to [read this]("http://www.brunolinux.com/04-The_File_System/Primary_Extended_and_Logical_Partitions.html").

Phantomdagger,

If you want to install grub to the bootsector of your ubuntu root partition, sda6, then you would do

> sudo grub-install /dev/sda6

(or hda6)

Or 

> sudo grub

> root (hd0,5)
> setup (hd0,5)
> quit

(Grub starts counting partition #'s at 0, so you subtract 1 from the partition.  Hence sda6=hd0,5)

Are you trying to chainload ubuntu using another distro's grub, or windows bootloader?

---

