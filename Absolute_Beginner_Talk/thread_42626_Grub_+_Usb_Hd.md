---
title: "Grub + Usb Hd"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by morficus on 2005-06-18
I just finished intalling Ubuntu onto my USB HD. All was fine... until I turned off the drive...
Now if I turn on my PC with the USB HD off... GRUB goes crazy (error 21). The only way to get around this is by turning on the USB drive, then shuting it down after Windows has loaded... and this is very anoying..  :-x  ]

Is there anyway to fix this?

While I'm here.. is there a way to get GRUB out of my master boot record? I was wondering if that was the problem... but then again.. I'm a noob to Linux, so I could be wrong.

---

### Post by Mez on 2005-06-18
Grunb on your MBR will look for the rest of the grub files on the USB drive, which is why it's going crazy

If you havea  windows XP disk, then boot off it and hit "r" when asked to enter a recovery console.

once in the recovery console.... type "fixmbr" (without the quotes) to fix your master boot record.

However, you'll need to put grub/lilo on a floppy disk to be able to boot into linux.

---

### Post by morficus on 2005-06-18
is there a way to put GRUB on a thumb-drive and not a floppy??

---

