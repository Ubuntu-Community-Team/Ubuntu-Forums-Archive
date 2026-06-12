---
title: "grub bootloader doesn't recognize xp?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by jackiecanev2 on 2007-05-23
ok. ive been running fiesty for a while and i love it, but i need a few things in xp for school/work and i don't feel like messing with a wine installation. soo... i resized my fiesty partition, and installed xp. i reinstalled grub from the livecd, but now grub doesn't recognize my xp installation; it only boots ubuntu. i tried to manually add an xp option to /boot/grub/menu.lst but nothing seems to work! i REALLY don't want to have to install xp first then reinstall ubuntu.... i just got this thing exactly the way i want it! :)

ok, so it looks like this:

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10497    84317121   83  Linux
/dev/sda2   *       10498       14033    28402920    7  HPFS/NTFS
/dev/sda3           14034       14410     3028252+   5  Extended
/dev/sda5           14034       14410     3028221   82  Linux swap / Solaris

i tried adding these to /boot/grub/menu.lst (otherwise its only linux on menu.lst) but nothing works

title Windows XP
rootnoverify (hd0,1)
makeactive
chainloader +1

title   Windows XP
rootnoverify (hd0,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1



any ideas???

---

### Post by Borzo on 2007-05-23
Try this

title Windows XP
root (hd0,1)
makeactive
chainloader +1

---

### Post by jackiecanev2 on 2007-05-23
perfect!! thank you~

---

### Post by thunderkyss on 2007-06-01
Worked great for me too.

Thanks guys

---

