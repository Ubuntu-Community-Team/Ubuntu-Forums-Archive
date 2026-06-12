---
title: "Reinstall GRUB after upgrade to Yosemite"
date: 2015-02-13
forum: Apple Hardware Users
---

### Post by Yumi on 2015-02-13
Have a dual boot with 2 OS X partitions and 3 ext4 partitions for /, /home and swap. Worked, Ubuntu booted from Grub, OS X from EFI.

Yesterday I upgraded the OS X version to Yosemite. Worked, but now Grub is not showing up, I am unable to boot Ubuntu.

I assume that upgrading OS X overwrote GRUB. How can I reinstall GRUB or another method to boot Ubuntu.

Michael

---

### Post by Yumi on 2015-02-13
EDIT: Solved my own problem. What happened was that the boot order was reset to boot OSX first. Booted from the USB-Ubuntu live. In the terminal I did a "apt install efibootmgr" and then "sudo efibootmgr". With "efibootmgr -o 0,80" the boot order was restored to Ubuntu to boot first. Now GRUB comes up again, Ubuntu boots.

---

### Post by Bucky Ball on 2015-02-13
Good news. Please mark as solved to help future travelers. See the second link in my signature for how. ;)

---

