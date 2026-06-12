---
title: "Uninstalling Grub"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by bim54 on 2005-08-04
I installed Ubuntu Hoary 5.04 to my machine last night.  I set it up as a dual boot with my Windows XP.
If I want to uninstall everything including the Grub, which I assume did something with the MBR, how would I do that with the least amount of chance of messing something up.  I may want to try other distros or if I decide that Linux is not my cup of tea, I don't want to trash my XP.

Please be specific.
Thank You.

---

### Post by Ampersand on 2005-08-04
Not sure about uninstalling Linux completely, but there's no problem moving to a different distribution. The installer for your next distrobution should allow you to format the ubuntu partition and set up grub again.

---

### Post by Irony on 2005-08-04
Just restore the XP Bootloader;

*Boot from XP installation disk > press any key on prompt to boot from CD > after some time options appear, press R for recovery > press 1 for windows > enter if no password > at the command prompt type; fixmbr > y for yes > at command prompt type; exit > eject disc*

Then it will boot into XP, from there you can go;

*Start > all programs > admin tools > computer managment > disk management*

Locate your linux partitions then right click on them and delete partitions. You can then create them again as ntfs if you want.

For example this is my current partition set-up;

[http://www.ironclub.net/log/part2.png](http://www.ironclub.net/log/part2.png)

I would just restore my xp bootloader then right click on those light blue partitions and delete them. Or I could delete them first - I would then have to restore the XP bootloader because deleting the partitions would confuse the GRUB bootloader.

---

