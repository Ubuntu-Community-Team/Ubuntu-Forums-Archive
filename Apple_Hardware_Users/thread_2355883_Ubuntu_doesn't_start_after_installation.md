---
title: "Ubuntu doesn't start after installation"
date: 2017-03-17
forum: Apple Hardware Users
---

### Post by davide3 on 2017-03-17
Hi all, I have an hard disk with a free partition, an efi partition, a swap partiton and another big partition with some other stuff.

I tried to install ubuntu upon the free partition, but it says that it can't find the efi partition at boot time.

I need a suggestion please help me!!!

---

### Post by QIII on 2017-03-17
Hello!

Just for clarity, you are saying you created a /boot/efi partition?

---

### Post by davide3 on 2017-03-17
Yes now there is a fat32 partition with EFI Boot contents automatically written by the installation process.

**EFI/ubuntu/grub.cfg**

> search.fs_uuid 99e6ecc3-4381-454e-a710-aa133b390a39 root hd0,msdos2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

and the uid is the right root / newer installed ubuntu partition.

---

### Post by davide3 on 2017-03-17
These are the black screen error messages at the boot time:

> failed to open \efi\boot\grubx64.efi
failed to load image \efi\boot\grubx64.efi
failed to open \efi \boot\mokmanager.efi
failed to load image \efi\boot\mokmanager.efi

in the efi\boot I got only these files:

\efi\boot\bootx64.efi
\efi\boot\bootx64.efi.grb

The requested files are inside this folder: \efi\ubuntu
So I copied them inside the efi\boot directory.

---

