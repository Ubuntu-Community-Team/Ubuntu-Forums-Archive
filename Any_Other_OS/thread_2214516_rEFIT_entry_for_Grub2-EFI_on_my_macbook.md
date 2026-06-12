---
title: "rEFIT entry for Grub2-EFI on my macbook"
date: 2014-04-01
forum: Any Other OS
---

### Post by max-atak on 2014-04-01
Hi,
 
I want to do this:
rEFIT menu list bootcamp, macOS, and legacy grub2 entry.
Grub2 entry list his menu with Bootcamp using setpci for ahci and the 2nd gpu, with no others hardware pb.
 
i think I have to install grub2 in the FAT32 EFI partition like this : /EFI/BOOT/BOOTX64.EFI
But how ?
 
 
My HD looks like this :
 
Fat32 EFI system 200mb
HFS+ Mac OSx partition 339gb => _avec rEFIT installé dessus_
#Unknown partition 618,89mb hybrideMBR I think#
NTFS Bootcamp partition 64,11Gb
 
I really need to boot windows with a grub2 patched (using firmware vars) to enable ahci and the 2nd gpu in windows 7.
  I have so much docs about this on google but i'm a bit confused about  how to do this correctly, where find package, how to compile grub2 etc.
Anyone can help me to install grub2 without touching my partitions please.

---

