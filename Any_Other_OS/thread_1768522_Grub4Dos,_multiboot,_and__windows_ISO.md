---
title: "Grub4Dos, multiboot, and  windows ISO"
date: 2011-05-26
forum: Any Other OS
---

### Post by gypsumwolf on 2011-05-26
I am using grub4dos to boot iso files. It works perfectly fine for linux based iso's but when I do a windows 7 install disc iso it boots into the installer but when I try to install the o/s it gives me an error about cd drivers. Same with windows xp but it gives me BSoD error. Is there a way I can multiboot this?

```
title Windows 7 PRO 32-bit (9,615)
find --set-root /iso/Windows7Professional32bit.iso
map (hd0,0)/iso/Windows7Professional32bit.iso (hd32)
map --hook
chainloader (hd32)
boot
```

reference link: [http://www.themudcrab.com/acronis_grub4dos.php#tagISO]("http://www.themudcrab.com/acronis_grub4dos.php#tagISO")

---

### Post by gypsumwolf on 2011-05-26
I know I can use something like Yumi from pendrive linux to create a multiboot, but I need to manually do this for some reasons. By the way, the windows 7 works fine using the yumi program to make the usb boot disk. I tried extracting the files to usb like the program does and the furthest I got was missing NTLDR.

---

