---
title: "How to erase the Grub Loading Stage1.5"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by fengjing99 on 2007-06-07
Does anyone know how to erase the Grub Loading Stage1.5? I have installed Windows Vista, followed by Ubuntu 7.04. Now I formatted the entire hard drive. But I can't get rid of the Grub Loading Stage. Now I am trying to install Windows XP, but the loading stage prevent me from start from the hard drive.
Thank you very much!
Feng

---

### Post by rich.bradshaw on 2007-06-07
That's part of grub loading.

If boot from Windows disk, go to recovery console and type

fdisk /mbr

then restart it will be gone. Grub installs into the MBR of the drive. If you just boot from the Windows XP install CD though, it will replace it automatically.

i.e. this isn't the problem you have. You need to tell your bios to boot from the cd before the hard drive.

---

### Post by fengjing99 on 2007-06-07
Thanks, rich. I can boot from the cd-rom. But when I finished the installation and ready for the reboot from the hard drive, it couldn't reboot without using bootable CD. I am trying your method of clearing the mbr.
Thanks again!
Feng

---

