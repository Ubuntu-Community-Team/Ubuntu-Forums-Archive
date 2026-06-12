---
title: "Grub Install Failed."
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Blaze 3.0.2 on 2007-01-23
Whenever I try to install Ubuntu onto my computer, it shows me a message warning me about how GRUB freezes or hangs on an xfs filesystem. I clicked "continue," and then this message pops up:

[[img]http://img255.imageshack.us/img255/3743/screenshot1va.th.png[/img]](http://img255.imageshack.us/my.php?image=screenshot1va.png)

At first, the hd4 was an ext3 filesystem. The installer formatted it to an xfs filesystem during the installation. I made sure GRUB would install to (hd4.) I am also attempting to preform a dual-boot with Windows XP.

---

### Post by housam on 2007-01-24
Try to reformat it to ext3 using Gparted and during the installation when it comes to the partitioning , choose to do it manualy.

---

