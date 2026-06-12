---
title: "Grub upgrade help"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-02-28
Hi, i'm in feisty and just upgraded my kernel to 2.6.20 -8 along with the latest grub version. It installed the new grub but did not activate. It said when i installed grub that grub now starts partitions with "1" not "0". However this version of grub has not been activated. It is using the old one. The old one is using menu.lst for it's config file. This does not have 2.6.20 -8 kernel in it. As of installing the new version of grub it boot a grub.cfg in /boot/grub and that does have the 2.6.20 -8 kernel. This means that it is using the old version of grub not the new one. I have tried to activate the new grub but can't figure out the right command for grub-install. Originally i tried just grub, so i could go into the grub terminal like i do when i repair my grub from a backup disk, however there is no grub executable in /usr/bin or /usr/sbin so i can't start it. How do i make it use the new version of grub instead, ( i think through grub-install).

Sorry for the long report.

---

### Post by ajmorris on 2007-03-01
bump.](*,)

---

### Post by ajmorris on 2007-03-03
now i have upgraded the kernel again to 2.6.20 -9. I have now also tried the command grub-setup but still can't figure out how to activate the new version of grub.

---

### Post by rsambuca on 2007-03-03
Are you using another linux distro in addition to Feisty?  Feisty should be upgrading your grub every kernel change.

---

