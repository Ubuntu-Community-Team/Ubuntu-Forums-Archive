---
title: "Do I leave the .DMG file extension?"
date: 2013-01-03
forum: Apple Hardware Users
---

### Post by 122jdh on 2013-01-03
I'm trying to make a bootable USB for my IBook to load LUBUNTU. When I convert the ISO to IMG in terminal, the file is produced with the .DMG  file extension. Now in the guide it states it does this automatically so i just remove it (filename.img.dmg changes to filename.img). When I Execute the "sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m" command with the .img the IBook will not show the usb when I boot holding OPTION. Can I use the original file with the .DMG extension?

---

### Post by powerpcliberation on 2013-01-04
This is older info but it still works on 12:
[https://help.ubuntu.com/8.04/installation-guide/powerpc/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/boot-usb-files.html)

---

### Post by robvas on 2013-01-06
> **122jdh said:**
> I'm trying to make a bootable USB for my IBook to load LUBUNTU. When I convert the ISO to IMG in terminal, the file is produced with the .DMG  file extension. Now in the guide it states it does this automatically so i just remove it (filename.img.dmg changes to filename.img). When I Execute the "sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m" command with the .img the IBook will not show the usb when I boot holding OPTION. Can I use the original file with the .DMG extension?

The filename extension doesn't matter - you're writing the raw data in the file to the USB, not the file name.

FWIW I don't perform the diskutil step to convert the ISO downloaded from Ubuntu's website to an IMG file - and it still works.

---

