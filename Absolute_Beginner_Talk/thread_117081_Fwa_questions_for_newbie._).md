---
title: "Fwa questions for newbie. :)"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by bbchinho on 2006-01-14
YES! I want something now.

Therefore i'm interested in Ubuntu.
I'm a design student in Hong Kong. So first of all, sorry for my language. :)
Before install Ubuntu, i have few questions.
Please give me a help! Thank you.

I'm now using Windows XP SP2 in a P4 2.4G computer, with 1G RAM and 2 120GB Harddisk both formatted in NTFS.
Every partition in those harddisks have it own usage for me. But i don't mind to format one partition of them for my new friend - Ubuntu. 
As my research before, Ubuntu isn't able to install in a NTFS partition, right? So could i format a partition to FAT32 for Ubuntu to setup? or simply in can install Ubuntu in C: together with my Windows?
Is that i am able to make a multiboot loader for Ubuntu and XP which i can select windows and Ubuntu to use while my PC boot up? If yes is the loader called GNOME?

That's call of my questions!
Thank you, my friend.

P.S. The ubuntu live cd is reallly good!
so attrative for a new user to change to ubuntu! :)

---

### Post by steve.horsley on 2006-01-14
Just delete the partition and leave free space. The ubuntu installer can format that space as required, and will generally make 2 partitions from it - a system partition and a swap partition.

Be careful with the partition options - the default is to erase and use the whole disk for Ubuntu.

And take backups first.

---

### Post by Maccabee on 2006-01-14
> 
 So could i format a partition to FAT32 for Ubuntu to setup? or simply in can install Ubuntu in C: together with my Windows?
i think you cant install Ubuntu on FAT32 you should install it on EXT2 or EXT3 file sysem.
> 
Is that i am able to make a multiboot loader for Ubuntu and XP which i can select windows and Ubuntu to use while my PC boot up? 
By installing it on EXT file system you can have a system with dual boot options one to your XP and other to your new friend Ubuntu

> 
 is the loader called GNOME?
GNOME is the X window MAnager similar to KDE. It provides a Desktop environment with GUI.
the boot loader with Ubuntu is normally GRUB( GRand Unified Bootloader)

---

