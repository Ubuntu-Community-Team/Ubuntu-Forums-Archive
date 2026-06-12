---
title: "Is my Mac Booting With EFI GRUB?"
date: 2010-02-11
forum: Apple Hardware Users
---

### Post by Ravernomina on 2010-02-11
hello all. I just install ubuntu Linux fully on my computer. Now i then install Grub-EFI, and EFI amd64. I also blessed my Linux partition. Now did i install everything to boot grub EFI? if i did. how do i know im booting using Grub EFI and not GRUB? Thanks!
Ravernomina

---

### Post by Ravernomina on 2010-02-12
Bump

---

### Post by linuxopjemac on 2010-02-12
I don't understand your question.

---

### Post by CJN on 2010-02-12
I wanted to achieve what you seem to be aiming for too, however the reason I didn't complete this project was that Apple uses a non-standard proprietary branch of EFI that doesn't play nice with either Windows 7's EFI compatibility or Ubuntu's.

However I will be watching this thread to see if you get it working, good luck.

edit: I am using a hybrid EFI/pseudo-mbr setup right now that works great, but that's not what you wanted so I won't go into detail.

---

### Post by tom4everitt on 2010-02-13
> **Ravernomina said:**
> hello all. I just install ubuntu Linux fully on my computer. Now i then install Grub-EFI, and EFI amd64. I also blessed my Linux partition. Now did i install everything to boot grub EFI? if i did. how do i know im booting using Grub EFI and not GRUB? Thanks!
Ravernomina

If you instantly get to the grub menu you probably succeeded. If you still get to the rEFIt menu or whatever you used before, you probably didn't :)

Here's a guide on how to efi boot a mac with grub2:
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

---

