---
title: "Ubuntu Grub before Refit (triple boot)"
date: 2012-05-04
forum: Apple Hardware Users
---

### Post by thinktyler on 2012-05-04
My current install boots directly into Grub and if I want to boot into OSX or Windows using Refit, then I hold option key during the boot process. 

My friend wants GRUB to boot first, but I'm unable to figure out how I did it.

Can anybody point me in the right direction?

---

### Post by kidhudi on 2012-05-05
if you reinstall grub it should make itself boot first.

---

### Post by Paul S on 2012-05-09
Try in a terminal:

1. sudo apt-get install grub-efi
2. sudo grub-install
3. sudo mount /dev/sda1 /mnt
4. sudo mkdir -p /mnt/EFI/BOOT/
4. sudo cp /boot/grub/grub.efi /mnt/EFI/BOOT/BOOTX64.EFI
5. reboot and hold Option key and select "efi"
6. to make it boot first, from osx terminal.app: "sudo bless --device disk0s1 --setBoot --verbose"

---

### Post by edgargdl on 2012-05-12
Hi All, 

I am really struggling with my ubuntu on my imac, there is no linux icon appearing but instead is a windows icon, even if i clicked is not opening linux..

here is the info of my partitions, am i doing something wrong?


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    487956615  Mac OS X HFS+
 3      487956616    489226151  Mac OS X Boot
 4      489226152    889204667  Basic Data
 5      889204668    929105058  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    487956615  af  Mac OS X HFS+
 3      487956616    489226151  ab  Mac OS X Boot
 4      489226152    889204667  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 487956616:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot

Partition at LBA 489226152:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 889204668:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap


** i am using refit by the way**

---

