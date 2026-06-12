---
title: "ubuntu in portable HDD"
date: 2012-03-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by zkrpar on 2012-03-25
I have laptop asus a42f which has win7 32bit. Now i have installed Ubuntu 10.04 in a portable HDD Using the laptop. Now my laptop does not boot win 7 if the portable Hdd is disconnected. i only get the boot option when portable HDD is conected. How will i run my laptop without the portable HDD? I also cannot use the portable HDD to another PC or laptop TO boot with it. please Help..........

---

### Post by gbrainin on 2012-03-25
It sounds like you used the normal installation process for Ubuntu, which replaces the MBR on the first hard drive.  Assuming you have a Windows 7 disc, it should be fairly easy to restore the Windows 7 MBR, which should allow you to boot without the portable drive in place.

As for installing Ubuntu on an external hard drive, it's doable, but you need to look for instructions specific to external hard drives in order to avoid the sort of problem you're now having.

---

### Post by collisionystm on 2012-03-25
Whenever installing to an external HDD, you need to disconnect your main hard drive and run the install with only the external attached. This will insure grub/mbr is installed on that drive. Grub has a mind of its own and is a disease to hard drives that have Windows.

---

### Post by oldfred on 2012-03-25
You can do it manually with these:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

This may make it a bit easier:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

This is a total walk thru of the repair process:
Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Grub remembers which drive to reinstall on major updates, I only think the last one includes that fix, or else you may find later you have to fix it again.

Or this will update which drive grub uses:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

