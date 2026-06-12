---
title: "Asus P8Z68-V Pro Boot Problem"
date: 2011-12-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by djrobthaman on 2011-12-07
Hi everybody,

Please help me if you can. I've installed 11.10 on my computer with the Asus P8Z68-V Pro montherboard installed with the followinig results:

At first I installed Ubuntu without any other OS and received a message saying "invalid arch independent elf magic" once I tried to boot.

Then, after much frustration, I installed Windows 7, which booted fine. Following that, I deleted the Windows partition and installed Ubuntu in its place. Now I get a message saying that the Windows boot manager can't find Windows.

Based on my searches, it seems to me (and please correect me if I'm wrong) that the issue I'm having has to do with some issues / incompatibilities with grub2 and this new fancy UEFI business.

Does anybody know what I can do to make ubuntu boot smoothly?

Thanks

---

### Post by rick6655 on 2011-12-09
I the only way I could get EFI booting to work was to install ubuntu from a USB drive. First power on then select boot options (mine is F8) during 'EFI / BIOS' screen, there will be 2 options for your USB drive. Select one with EFI next to it. Live mode is best as you will want to use gparted to change partition table to GPT. 
During installation you can either set partitions manually but have to add FAT16 partition or just select whole disk and let installer handle it for you. After installation boot as normal.
Other option is to just boot off a CD and install, EFI wont be installed.
One thing I noticed was that after a 'EFI / BIOS' update I could no longer boot into ubuntu. You then need to recover grub - boot off installation disk and repair grub.

---

### Post by oldfred on 2011-12-09
+1 Good first post from rick6655.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell


Grub has a few bugs and the bug reports do have some workarounds.
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
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

