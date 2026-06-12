---
title: "Install 20 on new Mac usb c fails at Grub step"
date: 2021-03-06
forum: Apple Hardware Users
---

### Post by gary1008 on 2021-03-06
I am trying to install Ubuntu 20.04 on a MacBook Pro 2019 external drive connected with USB c.
New Macs like this have known complications for installing Ubuntu.
Made the installation stick with unetbootin. Using refind as boot manager.
External drive is Samsung XS Portable with SSC
Install goes well until installation of Grub. Then just says Fatal Error.

Tried a few times, remaking install stick, etc. Always the same problem.

---

### Post by howefield on 2021-03-06
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by CelticWarrior on 2021-03-06
Have you done manual partitioning? If so, have you selected the ESP (EFI System Partition) as well?

---

### Post by gary1008 on 2021-03-07
I'm trying to use the whole drive. I erased it in Disk Utility and made it FAT. It didn't do the whole disk, but left some part out. Then in the Ubuntu install I selected that part - which was my only choice except the hard drive. I didn't do any other partitioning.

---

### Post by CelticWarrior on 2021-03-07
Linux can't be installed in FAT partitions, that step was unnecessary. Ideally you should have unallocated space, no partitions or file systems, the installer should then create all the required partitions.

When NOT using the options to "erase and install..." or "install alongside...", one must choose something else and then create the required partitions with proper file systems as well as select the already present ESP in any UEFI system. So, currently there's no need to create a swap partition (Ubuntu uses swapfile by default) which means that you need only to create the / (root) partition in the instended unallocated space and select to format as EXT4 (preferred) -and- select the ESP as "EFI" (don't format, obviously, and it won't give you that option anyway) that may or may not be in the same drive.

---

### Post by oldfred on 2021-03-07
If an external drive, you probably want an ESP - efi system partition on that drive.
Ubuntu's Ubiquity will only install to ESP on first internal drive.
You can then only boot external drive from UEFI ubuntu boot entry in the first internal drive.
But if you install grub to external drive, you can directly boot from external drive on any UEFI system.
(Not sure of differences with Mac vs. PC).

UEFI systems boot external drives from /EFI/Boot/bootx64.efi. This is how you have booted the UEFI installer.
With a full install a copy of shimx64.efi is put as bootx64.efi. But it also needs the extra boot files in /EFI/ubuntu.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

