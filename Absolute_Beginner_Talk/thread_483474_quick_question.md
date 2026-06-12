---
title: "quick question"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by lestial on 2007-06-24
how do i un-install ubuntu and the bootloader to return my computer to just a windows machine?

---

### Post by h0ax on 2007-06-24
if you dualbooted all you need to do is boot with the windows disk and re-install over the MBR(Master Boot Record)
If you're just trying to reinstall windows overtop of your Ubuntu install - then just put the disk in and go through the setup.
Sad you're leaving! :(

---

### Post by lestial on 2007-06-24
i don't have a windows disc actually. i'm not trying to reinstall windows, i just want to remove linux and lilo so i can get back INTO windows because right now.. i just can't.

---

### Post by Clay_Banger on 2007-06-24
to reinstall the windows boot loader, boot into a windows 98 startup disk and enter this command:
```
fdisk /mbr
```
then reboot your machine, it should load into windows.

if you dont have a windows 98 startup disk, you can download one from [here]("http://files.frashii.com/~bootdisk/newjersey/boot98se.exe").

---

