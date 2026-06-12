---
title: "Dual boot question:  upgrading mswind on slave..."
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-04-25
I dual boot with two hard drives, ubuntu on the master and win2k on the slave.  Suppose I want to upgrade win2k to windows xp or whatever, what do I do? I assume I just can't do an upgrade without destroying what grub put on the windows drive.
Thanks,
Michl

---

### Post by mikeyphi on 2007-04-26
> **Michl said:**
> I dual boot with two hard drives, ubuntu on the master and win2k on the slave.  Suppose I want to upgrade win2k to windows xp or whatever, what do I do? I assume I just can't do an upgrade without destroying what grub put on the windows drive.
Thanks,
Michl

That's right! If you upgrade windoze...by installiong a newer version it will overwrite the boot record and you would have problems booting into Ubuntu. You should do some research into the Grub bootloader. I believe it is possible to fix the bootloader using a Live CD..... Look here for a guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation)

---

