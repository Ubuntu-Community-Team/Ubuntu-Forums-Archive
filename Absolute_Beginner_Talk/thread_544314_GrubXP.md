---
title: "Grub/XP"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by davek17 on 2007-09-06
I installed XP on a seperate partition on my pc after i already had ubuntu installed.  Initially i found i couldnt get back into my ubuntu partition as it automatically booted up into windows.  Doing the live cd fixing of grub i now have to opposite problem where i cant access my xp partition as all the options in grub are ubuntu boot options and was wondering how to set it up to choose between windows and ubuntu.

Thanks

---

### Post by alienexplorers on 2007-09-06
Add this to your grub file at the end:
> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Change the root location to match the location of XP on your system.

---

### Post by philinux on 2007-09-06
Just in case you dont know how to access the grub file type this in terminal.

gksudo gedit /boot/grub/menu.lst

You will see sample windoze boot entries commented out too.

---

### Post by davek17 on 2007-09-06
How do i know what partition it is on?

---

### Post by alienexplorers on 2007-09-06
in terminal type sudo fdisk -l

---

