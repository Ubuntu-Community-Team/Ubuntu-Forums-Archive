---
title: "boot-repair Live CD not fixing problem"
date: 2013-12-22
forum: Any Other OS
---

### Post by johnnydoe on 2013-12-22
I have two separate HDDs...one boots Windows 8.1 and the other boots Ubuntu. It was working fine the last couple of weeks, but now it won't boot into Ubuntu even after running boot-repair.  I am attaching the boot-repair LiveCD report.  [http://paste.ubuntu.com/6619490/](http://paste.ubuntu.com/6619490/)

---

### Post by oldfred on 2013-12-22
Moved to other OS since Mint. Do not know what differences that may make.

Your BootInfo report shows no Windows drive. And the efi partition in the Windows drive is probably where Ubuntu installed its UEFI boot files.
Your efi partition on sda1 shows no boot files for UEFI and just a copy of core.img.

---

