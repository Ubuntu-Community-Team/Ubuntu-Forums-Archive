---
title: "Grub?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-03-09
OK, I know that GRUB is automatically installed when you are installing ubuntu, but what I am asking is where it should be installed, should it be installed on the linux HDD, or the windows one? And once it is installed from the ubuntu installation, there is no manual configuring I need to do?
thanks for the help



-sewercake

---

### Post by igknighted on 2007-03-09
It doesn't matter where it gets installed, as long as after its installed you tell the bios to boot to that disk.  I would recommend not putting it on the winXP drive, as it would overwrite winXP's bootloader.  This will likely mean you have to swap the boot order in the bios though.

There shouldn't need to be any manual completion, but every now and then automated scripts make mistakes, so you never know.

---

### Post by dstew on 2007-03-09
Excellent question. Grub needs to know two things to be installed correctly. First, where does the booter go? Second, where will grub find its stage 2 and configuration files at boot time?

The answers to these questions depend on the the disk configuration of your system. If you have only one disk, then you will install grub on its MBR by chosing hd0 as the place to install, and then hd0,0 or hd0,1 as grub's root, depending on which partition will have the linux file system.

If you have two or more disks you have to be a little careful. If your first disk is your windows disk (hd0), I would recommend installing grub there. All this does is put grub stage 1 into the master boot record of the windows disk. Sure, it overwrites the first part of the windows booter, but grub can boot windows just fine, and if you want you can remove grub later and restore the windows native booter by opening the windows recovery console and using the fixmbr command. The grub root partition would be on the second hard disk, (hd1) where linux is. If you have only the usual root, and swap partitions, make the grub root  same as the linux root (hd1,0 for the first partition). If for some reason you have a separate boot partition, then make that the grub root.

If you have two disks and the first disk is your linux disk, put grub there also, and leave the windows disk untouched. You can still boot the windows disk from grub, but you will need to edit the grub configuration file /boot/grub/menu.lst to fool the windows disk into thinking it is number one, using the map command.

---

