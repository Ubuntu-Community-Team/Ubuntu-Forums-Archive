---
title: "refit icons and grub"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by asymmetric on 2008-07-29
hi!

during the installation phase, i inadvertently selected (hd0) as the drive where to install grub, resulting in a pretty icon of tux which didn't actually  work..

then, using the livecd, i remedied by reinstalling grub via these 2 commands:

```

root (hd0,2)
setup(hd0,2)
```

when i reeboted, i had to icons in refit, the first which didn't work, and the second which worked perfectly.

so, how do i remove the first, wrong installation of grub (or simply the icon maybe)?

thanks
asy

---

### Post by cyberdork33 on 2008-07-29
Actually, having GRUB installed to the MBR is OK... There is nothing wrong with that, but if you triple boot, only one bootloader can occupy that location (GRUB or Windows Bootloader).

Here is how you can clear the MBR bootcode:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

---

