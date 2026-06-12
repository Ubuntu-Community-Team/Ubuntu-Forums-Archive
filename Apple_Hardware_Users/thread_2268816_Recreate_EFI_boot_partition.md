---
title: "Recreate EFI boot partition"
date: 2015-03-11
forum: Apple Hardware Users
---

### Post by Tyler_MacPherson on 2015-03-11
In short, I accidentally killed my EFI boot partition for my Ubuntu installation on my MacBook Pro and now it doesn't boot at all. I have an Ubuntu 14.04 live USB that I can use. My question is, how to I go about remaking the boot partition so that I am able to boot again?

Thanks!

EDIT: I should also mention that there is no OS X partition, just Ubuntu.

---

### Post by oldfred on 2015-03-11
I do not know if there is some difference or not.

Standard efi partition is FAT32 formatted usually about 300MB, but Windows creates 100MB as default, others suggest up to 600MB. And it has to have boot flag if using gparted. Or if using gdisk code ef00 to make it the ESP partition.

If you have a backup of the old one, you should just have to copy files back. Not sure then how a Mac's UEFI works.

Boot-Repair can do a full uninstall and reinstall of grub, which should recreate all the files in the efi partition.  Or you should be able to chroot into install and do the totally reinstall of grub.

some links on Macs:
 [http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

