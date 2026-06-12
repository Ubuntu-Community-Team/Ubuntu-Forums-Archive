---
title: "[Emergency]xUbuntu trying to setup win 7 on pendrive"
date: 2011-09-17
forum: Any Other OS
---

### Post by kemc on 2011-09-17
Hy!

I'm using xUbuntu 11.04 on laptop (Acer Aspire 5520) but i have another computer where i want to setup Win 7. i have problem,on my laptop i have Win 7 iso image and i can't find way how to make bootable usb from it (like making bootable usb ubuntu on windows) i searched on google and on yahoo answers but i can't find anywher so please if you can help me. It's emergency because i need computer for school and must be fixed ASAP.

Sorry for my bad grammar and please help me :)

---

### Post by SirDrexl on 2011-09-17
Install Unetbootin.  It's pretty easy to select your ISO and get it on the USB flash.

But first, make sure you format the USB stick as NTFS.  Apparently it  needs to be in that format, at least in some cases (and that was my  experience as well).

---

### Post by kemc on 2011-09-17
> **SirDrexl said:**
> Install Unetbootin.  It's pretty easy to select your ISO and get it on the USB flash.

But first, make sure you format the USB stick as NTFS.  Apparently it  needs to be in that format, at least in some cases (and that was my  experience as well).

Thanks for quick response :)

---

### Post by kemc on 2011-09-17
> **SirDrexl said:**
> Install Unetbootin.  It's pretty easy to select your ISO and get it on the USB flash.

But first, make sure you format the USB stick as NTFS.  Apparently it  needs to be in that format, at least in some cases (and that was my  experience as well).
when i tried to format i get this /dev/sdb1 is mounted

edit1: i fixed it [FONT=monospace][/FONT]sudo umount /dev/sdb1 and that was it :)

---

### Post by kemc on 2011-09-17
> **SirDrexl said:**
> Install Unetbootin.  It's pretty easy to select your ISO and get it on the USB flash.

But first, make sure you format the USB stick as NTFS.  Apparently it  needs to be in that format, at least in some cases (and that was my  experience as well).
new problem has accured i formated USB as NTFS unetbootin didn't find it then i format as FAT32 it didn't find it either i mounted it back everytime

---

### Post by SirDrexl on 2011-09-17
Did you try the option to show all drives and verify that the device ID  of your USB flash drive was correct?  Check Disk Utility to find out what it is, then pick the same one in Unetbootin.  On my computer, it gets "sdd", but it  looks like sd5 would be used if I relied on automatic detection.

Be careful to choose the correct device.

---

