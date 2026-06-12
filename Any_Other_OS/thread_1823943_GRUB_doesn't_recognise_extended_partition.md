---
title: "GRUB doesn't recognise extended partition"
date: 2011-08-12
forum: Any Other OS
---

### Post by wsmccusker on 2011-08-12
I currently have 4 OS's installed:
Windows 7
Mac OS X
Ubuntu
and Fedora

Fedora was installed last, write it to the MRB, as it is part of the extended partition.

Does anyone have any ideas on how to get GRUB2 to recognise the extended partition without me needing to reinstall fedora or any of the other OS'?

I much prefer the GRUB2 Interface than the fedora one. Or maybe I could install chameleon as that bootloader is brilliant.

---

### Post by donato roque on 2011-08-13
I like using GRUB2 because it's easier to add another OS after I install it:

root # update-grub

check by a reboot.

---

### Post by wojox on 2011-08-13
Reinstall [Grub2]("https://help.ubuntu.com/community/Grub2#Copy LiveCD Files")

This should work fine unless you used LVM, in which case you will have to chainload.

---

### Post by wsmccusker on 2011-08-13
> **donato roque said:**
> I like using GRUB2 because it's easier to add another OS after I install it:

root # update-grub

check by a reboot.

I tried this but it doesn't work. It doesnt add to the OS list

---

### Post by PCaddicted on 2011-08-14
> **wsmccusker said:**
> I currently have 4 OS's installed:
Windows 7
Mac OS X
Ubuntu
and Fedora

Fedora was installed last, write it to the MRB, as it is part of the extended partition.

Does anyone have any ideas on how to get GRUB2 to recognise the extended partition without me needing to reinstall fedora or any of the other OS'?

I much prefer the GRUB2 Interface than the fedora one. Or maybe I could install chameleon as that bootloader is brilliant.
On Apple hardware or non-Apple hardware?

---

