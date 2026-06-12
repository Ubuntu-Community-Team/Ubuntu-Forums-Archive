---
title: "bootable iso daemon"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by spearo on 2008-03-29
Ok here is my problem. I have downloaded ubuntu server enterprise and have no cd's or dvd's to copy teh image file onto. Is there a way that i can mount the bootable image. 

i have tried sudo mount -t iso9660 -o loop <FILENAME.iso> /media/cdrom   and it works to some effect except it just lets me browse teh folders in teh image and not start a boot up sequence for me to install teh software.

Is there a way this can be done (i could wait till tomorrow to buy cd's) but if there is an alternative i'll be glad if you can help.

Kind regards

Liam

---

### Post by Daveth on 2008-03-29
if your bios supports booting from a usb stick, you could stick the iso on that, set it to first boot priority, and off you go.

---

