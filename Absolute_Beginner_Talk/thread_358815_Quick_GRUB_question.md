---
title: "Quick GRUB question"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by antihero on 2007-02-11
Hey, I deleted one of my partitions that was causing problems.  It was /dev/sda5.  When I rebooted I can no longer boot into Ubuntu.  When I select my kernel from the boot menu I get Error 15, file not found.  It seems like GRUB thinks Ubuntu is still sda6 but now its located on sda5.

How make GRUB point to the correct location where Ubunutu resides?

Thanks.

---

### Post by sas on 2007-02-11
> **antihero said:**
> Hey, I deleted one of my partitions that was causing problems.  It was /dev/sda5.  When I rebooted I can no longer boot into Ubuntu.  When I select my kernel from the boot menu I get Error 15, file not found.  It seems like GRUB thinks Ubuntu is still sda6 but now its located on sda5.

How make GRUB point to the correct location where Ubunutu resides?

Thanks.

You can press 'e' on the kernel line in grub and then find the bit where it says /dev/sda6 and replace it with /dev/sda5 (I think it says root=/dev/sda6 at the minute)

---

### Post by mikewhatever on 2007-02-11
The suggestion above should work, but for one boot only. Once you have found the correct number and booted, edit grub menu to make it permanent.
> cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

---

