---
title: "Unstall UBUNTA, how to"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by AnnBrady on 2006-09-09
I have been using Ubunta with a single HD, (three partitions) dual boot and it works pretty well. However, I have recently bought a new computer, giving the old one to a not for profit group who's computer failed. 

I really don't care if I uninstall Ubunta or not, but I need for it to start in Windows as the volunteers who will be using it are not too computer savy. So I need to uninstall it or change GRUB on startup

Thanks for any help

---

### Post by Tomosaur on 2006-09-09
You can make Windows the default by tweaking a few settings in Grub:
You can set Windows to load by default.
You can lower the Grub timeout.
You can hide the Grub menu completely.

All of this can be done by editing /boot/grub/menu.lst, or you can download the script in my sig to make it a bit easier.

---

### Post by curtisf14 on 2006-09-09
You could also install the Windows boot loader to replace GRUB.  To do this, just insert the Windows XP setup disk and choose to repair Windows.  You should probably only do this if you really don't want to boot to Ubuntu anymore.

---

### Post by AnnBrady on 2006-09-09
Thanks, I will try them

---

