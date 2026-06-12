---
title: "Bootloader Problem"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by USR612 on 2007-05-04
Hi

     A failed install of Dapper Drake has led to my computer loading up nthe GRUB bootloader, letting me select either Vista or Ubuntu, but ubuntu doesn't work.  I've had much help o this issue, but can't seem to get it working.  What I would like to do now, is uninstall the remnants of ubuntu and reinstall the Vista bootloader, then install Feisty Fawn.  Whenever I try to reinstall the Vista bootloader however, GRUB still comes up when I turn on/reboot my computer.  Would deleting/clearing the linux partition solve this problem? or lead to a computer with no bootloader.  I don't mind deleting the linux partition, as I didn't make it large enougg, so I'll have to modify it anyway.
Any help is much appreciated!

Note: I'm completely new to linux, so you'll have to forgive any errors/stupidity.

Thanks

---

### Post by starcraft.man on 2007-05-04
> **USR612 said:**
> Hi

     A failed install of Dapper Drake has led to my computer loading up nthe GRUB bootloader, letting me select either Vista or Ubuntu, but ubuntu doesn't work.  I've had much help o this issue, but can't seem to get it working.  What I would like to do now, is uninstall the remnants of ubuntu and reinstall the Vista bootloader, then install Feisty Fawn.  Whenever I try to reinstall the Vista bootloader however, GRUB still comes up when I turn on/reboot my computer.  Would deleting/clearing the linux partition solve this problem? or lead to a computer with no bootloader.  I don't mind deleting the linux partition, as I didn't make it large enougg, so I'll have to modify it anyway.
Any help is much appreciated!

Note: I'm completely new to linux, so you'll have to forgive any errors/stupidity.

Thanks

You don't have to do anything fancy, just download the Feisty Fawn cd (Alternative or Live CD) and then boot into it and overwrite your root directory with Feisty (make sure you select reformat when you remount root). There shouldn't be any problem. GRUB should autodetect Vista once your finished the install.

That should be it, have fun with feisty.

---

### Post by USR612 on 2007-05-05
Thanks for the tip!

---

### Post by starcraft.man on 2007-05-05
> **USR612 said:**
> Thanks for the tip!

Your welcome, have fun with Feisty :D

---

