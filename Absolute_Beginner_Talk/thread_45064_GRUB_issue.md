---
title: "GRUB issue"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by tomd on 2005-06-28
I installed Ubuntu 5.04 on my pc with Windows XP and allowed the installer to put GRUB in the MBR. But when I restart, Windows loads and GRUB does not appear. Why is GRUB not starting? How can I fix this?

---

### Post by manicka on 2005-06-28
Use the install disk to reinstall Grub.

---

### Post by tomd on 2005-06-28
On the install cd I selected "Install Grub bootloader" but it gives an error that a step failed. Where can I find instructions on re-installing Grub from the install cd?

---

### Post by manicka on 2005-06-28
Dou you remember what the error message said? Which step failed?

---

### Post by tomd on 2005-06-28
Trying to reinstall Grub from cd:
>at menu I selected "install the GRUB boot loader"
>Goes to partition manager, I select back. Do I have to select the ubuntu partition?
>Error: "Install Base System - no file system mounted on /target

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=tomd] Do I have to select the ubuntu partition?[/QUOTE]

yes

---

### Post by manicka on 2005-06-28
I'm working a bit from memory here, but I think you need to configure the partition manager at this stage instead of selecting back. Set the mount points for each of your partitions manually. Just make sure that you select to ***_not_*** repartition your drives. Grub should then run at the end of that process.

---

### Post by tomd on 2005-06-28
How do I set the mount points?

---

### Post by manicka on 2005-06-29
[QUOTE=tomd]How do I set the mount points?[/QUOTE]
 there should be an option to set the mount points when you select the partition

---

