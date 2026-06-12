---
title: "Dual Boot and Partition questions"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Bli on 2006-09-13
currently i run xp and have been for many years.
so i have a couple questions about installing ubuntu.

When i partition, do i do it as primary or logical? After i partition, i simply burn the iso and put it in the cd-drive and reboot right? Do i install grub after i install ubuntu?

---

### Post by jordanmthomas on 2006-09-13
The CD will do the partitioning for you (if that's what you want...you're free to do it yourself).
You just burn the iso, boot off the CD (don't forget to tell your BIOS you want to boot off the CD drive) and go to Install if you like it.
It will install GRUB for you at the end of the installation.

For the record, Ubuntu put its main files on a primary partition and the swap on an extended (logical) partition but you can do it however you want.  Just remember you can only have 4 primary partitions

---

### Post by bodhi.zazen on 2006-09-13
[list=number][*]Primary partitions are fine. Logical will work as well.
[*]Grub installs as part of the ubutuntu install.
[*]Burn & boot (may need to update BIOS to boot from CD)[/list]

Guide:

[Graphical Ubuntu Install guide](http://www.psychocats.net/ubuntu/installing.html) [color=red]Thanks aysiu[/color]

---

