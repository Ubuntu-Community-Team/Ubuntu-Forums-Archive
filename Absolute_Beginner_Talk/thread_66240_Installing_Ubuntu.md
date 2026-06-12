---
title: "Installing Ubuntu"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by palnasen on 2005-09-16
I have Intel platform, 3 logic disks and I want to install Ubuntu on disk e:

How can I do this without formatting other disks and with multi-boot menu on startup

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=palnasen]I have Intel platform, 3 logic disks and I want to install Ubuntu on disk e:

How can I do this without formatting other disks and with multi-boot menu on startup[/QUOTE]


When it gets to the guided partitioning, tell it you want to "manually edit partition table." Then select the drive you have to install Ubuntu on, hit enter. You want it to be a etx3 partition and you want it formatted, and you want it mounted on "/" Just write this down if you don't know what I'm talking about, just as long as the you pick the right options.

The "write changes to disk."

---

### Post by aysiu on 2005-09-16
And don't forget to install Grub to the MBR.

---

