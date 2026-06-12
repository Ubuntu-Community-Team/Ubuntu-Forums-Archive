---
title: "Ubuntu from external SSD not booting on MacBook Pro 13&quot; 2017"
date: 2017-11-25
forum: Apple Hardware Users
---

### Post by tsarshah on 2017-11-25
I've installed Ubuntu 16.04 LTS on an external SSD. Due to less number of ports, I decided to install Ubuntu in my external SSD using my iMac. It is working fine there. But when I plug in the same SSD to the MacBook Pro, the purple Ubuntu screen pops up, and it hangs. It does not work on it.

---

### Post by slickymaster on 2017-11-25
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by oldfred on 2017-11-25
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Mac uses UEFI, but grub only installs to ESP on drive seen as sda or first drive if NVMe or other types.
So your install system may have grub in it, but not on SSD.

I do not know Mac, but with PC, you have to have an ESP and copy files to ESP on external drive to allow it to boot directly from external drive.
UEFI only boots from /EFI/Boot/bootx64.efi file. But grub installs to /EFI/ubuntu/ and has shimx64.efi or grubx64.efi. 

Do you have an ESP on SSD? FAT32 with boot flag?

---

### Post by mfox on 2017-11-26
I suspect that this has to do with the video card in your Mac, as I have experienced the same with a Late 2015 iMac that contains a Radeon video card. Assuming that you are accessing the drive by hitting the option key on your MBP, when you get the menu up for trying or installing Ubuntu, hit the "e" key, which allows you to edit the grub. If you add "nomodeset" as a parameter on the grub line right after the words "quiet splash", it should boot up. At least it did for me.

---

