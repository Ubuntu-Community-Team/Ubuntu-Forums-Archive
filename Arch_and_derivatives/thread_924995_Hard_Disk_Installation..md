---
title: "Hard Disk Installation."
date: 2008-09-20
forum: Arch and derivatives
---

### Post by kagashe on 2008-09-20
I am trying to install using swap partition on my hard disk as per instructions on [this page]("http://wiki.archlinux.org/index.php/Hard_Disk_Installation") on ArchWiki but the installer does not boot. The page suggests to add the following in /boot/grub/menu.lst of present installation:
> title ArchLinux Installation System
root (hd0,1)
makeactive
chainloader +1Is this correct?

kagashe

---

### Post by Barrucadu on 2008-09-20
Yes, you need to add that to your current GRUB menu.lst to be able to boot the installer - assuming that (hd0,1) is the partition you put the installer on.

---

### Post by kagashe on 2008-09-20
Instead of chain loading I decided to boot directly through the following entries:
> title		ArchLinux Installation System
root		(hd0,1)
kernel 		/boot/vmlinuz26 lang=en locale=en_US.UTF-8 ramdisk_size=75%
initrd 		/boot/archlive.imgand it works.

kagashe

---

