---
title: "Mac Mini Mid 2007 and grub (interesting behaviour)"
date: 2012-08-19
forum: Apple Hardware Users
---

### Post by DigiAngel on 2012-08-19
So..I've got 12.04 working and installed fine on my Mac Mini Mid 2007.  Something curious I noticed though.  When I do a full install, and install grub to /dev/sda4 (now triple booting this beast), everything works fine.  So just for testing, I rebooted going to Rescue Mode and try to do a reinstall grub to /dev/sda4, and if fails on the setup that was just successful with a full install.  So my question is, what's the difference between the installers grub, and Rescue Mode's grub?  Thanks all.

---

### Post by snip3r8 on 2012-08-21
Just sucking ideas out of the air here ,but doesn't rescue mode disable a lot of drivers? If it does maybe it requires one of those disabled drivers to run on that particular hardware. Would be interesting to see if this problem occurs with other Macs or just the Mac-mini.

---

