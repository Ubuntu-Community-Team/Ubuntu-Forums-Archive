---
title: "Recover windows?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by siongz on 2007-11-28
hi... im a new linux user and when i install Ubuntu, i put everything to automatic cos i dont really understand those codes that they use,
so if im not wrong ive accidentally overwrite my windows files... so is there a way i can recover the lost windows partition? 

please help me on this... thx (sorry for being a newb):confused:

---

### Post by oeolycus on 2007-11-28
If you put everything on automatic, you probably shrunk the Windows partition and installed Ubuntu. You may need to add Windows to your GRUB, but before we do that, would you punch the following into an Ubuntu terminal: ```
sudo fdisk -l
```

That will tell us if there's still an NTFS partition onboard.

---

### Post by santiagoward2000 on 2007-11-28
Do you mean you completely overwrote you Windows partition with Ubuntu? Well, I hope I'm wrong, but as far as I know you can't get them back, sorry?
Haven't you made a backup before trying to install Ubuntu? You could reinstall Windows, but I believe there's no way you can get your personal files back... :(

---

### Post by siongz on 2007-11-28
It says this...

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe233bc5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

---

### Post by oeolycus on 2007-11-28
That very much sounds like you overwrote your NTFS partitions. Recovering THAT information is beyond my scope of knowledge unfortunately. I'm very sorry.

---

### Post by siongz on 2007-11-28
Alright... thx a lot btw...

---

