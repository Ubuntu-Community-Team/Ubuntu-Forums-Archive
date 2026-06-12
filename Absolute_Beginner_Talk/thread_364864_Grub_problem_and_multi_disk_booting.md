---
title: "Grub problem and multi disk booting"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by mikeescott on 2007-02-18
I am getting an error 17 from Grub again after a fresh install. I tried to repair with Super  Grub to no avail. I did read in the documentation with Super Grum that there may be a problem if my bios supports booting from 2nd, 3rd, or im my case, 4th drive. My 1st drive is XP-64, my second drive is a backup drive for all of the other drives, the 3rd drive is XP, and the 4th is Ubuntu. I have always booted from the 3rd drive, wich is e-ide like the 4th and the 1st 2 are sata. I have tried changing the boot order of the drives to every combination and nothing works. I have reinstalled Ubuntu several time to get a good Grub and nothing worked. I have the option to push F8 during POST to choose a boot device. If I choose the Ubuntu drive, there is an error loading OS. If I choose the XP-64 drive, it loads ok. But, if I choose the XP drive, I get the error 17. What can I do here?

---

### Post by mikeescott on 2007-02-18
Is there a way to tell Ubuntu to boot as ab OS when that drive is selected as the 1st boot device?

---

### Post by confused57 on 2007-02-18
> **mikeescott said:**
> I am getting an error 17 from Grub again after a fresh install. I tried to repair with Super  Grub to no avail. I did read in the documentation with Super Grum that there may be a problem if my bios supports booting from 2nd, 3rd, or im my case, 4th drive. My 1st drive is XP-64, my second drive is a backup drive for all of the other drives, the 3rd drive is XP, and the 4th is Ubuntu. I have always booted from the 3rd drive, wich is e-ide like the 4th and the 1st 2 are sata. I have tried changing the boot order of the drives to every combination and nothing works. I have reinstalled Ubuntu several time to get a good Grub and nothing worked. I have the option to push F8 during POST to choose a boot device. If I choose the Ubuntu drive, there is an error loading OS. If I choose the XP-64 drive, it loads ok. But, if I choose the XP drive, I get the error 17. What can I do here?

You might want to consider restoring your Windows mbr on your 3rd drive, install grub to your 4th drive mbr & use F8 to select which OS to boot, similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

You can install grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
If you install grub to the Ubuntu drive's mbr & select this drive as the first boot device, you should be able to boot Ubuntu, by highlighting the Ubuntu in the grub menu, press "e" to edit, & change the root to (hd0,0), if root is on the first partition, then "b" to boot...if it works, this change is temporary...you'd need to make it permanent in your /boot/grub/menu.lst.

Even though you'd be using F8 to boot each individual OS, you could add entries to your grub menu to boot Windows, if you set your Ubuntu drive as the first hard drive booted:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Bumped your thread, if nothing else.

---

