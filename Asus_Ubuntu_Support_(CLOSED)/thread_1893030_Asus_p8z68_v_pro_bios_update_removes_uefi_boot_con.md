---
title: "Asus p8z68 v pro bios update removes uefi boot conf"
date: 2011-12-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by praxone on 2011-12-09
Single boot ubuntu 11.10 uefi  setup on P8Z68 V PRO.
Stopped booting after latest bios update.
UEFI Boot config is no more visible in bios info.
Boot hard drive is configured to boot.
Never saw uefi specific boot options in bios panel.
How can i recover ?

---

### Post by Repabil on 2011-12-09
I also have this problem. However, I managed to boot by setting the flag of the 20 MB partition before my boot partition to "bios_grub". I got error messages when booting, something about /boot/efi not being ready, I ignored it and got some further error message but after that I was able to login and I'm now writing this in Firefox on the affected system. This seems like a dirty solution. I hope someone knows a better way to solve this.

Oh and I found the following on Ask Ubuntu which seems to be about the same problem: [http://askubuntu.com/questions/86541/how-to-fix-boot-efi-not-ready](http://askubuntu.com/questions/86541/how-to-fix-boot-efi-not-ready)

---

### Post by oldfred on 2011-12-09
I think new UEFI systems check for the efi partition and if found boot in efi mode, if not found default back to MBR mode.

If booting with bios_grub you have reverted to MBR mode and grub2's core.img is installed to the bios_grub partition.

While not your models, they may give hints to solving issue:
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Grub has bugs with UEFI:
UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

