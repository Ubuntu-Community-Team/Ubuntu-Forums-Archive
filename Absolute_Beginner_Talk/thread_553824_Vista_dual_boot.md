---
title: "Vista dual boot"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Bookmarks on 2007-09-18
I'm new to linux and I want to give it try, but I'm a little worried about losing my Vista installation.
I want to install ubuntu on a different hard drive from my vista hard drive. I want to know will GRUB recognize vista on the separate hard drive. Is there a certain process I should follow?

---

### Post by skidkid87 on 2007-09-18
follow what's in this link and it should work fine (it did for me)

[http://www.apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://www.apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

when prompted for a HD space just select the hard drive u want and for best performance:
make a 10 GB partition for linux with the ext3 format 
another 2 GB for swap partition in the swap format
and another and 8 GB use as a /home directory in ext3 format

PS: use the formater in linux only after u make a space of 20 GB free by vista's partitioner

---

### Post by LaRoza on 2007-09-18
> **Bookmarks said:**
> 
I want to install ubuntu on a different hard drive from my vista hard drive. I want to know will GRUB recognize vista on the separate hard drive. Is there a certain process I should follow?

The safest thing to do is unplug the Vista drive while installing, however, you will have to manually add it to grub (which I did).

If you need to reinstall the Vista boot loader, and don't have a Vista install disk, use the Super Grub Disk. It is a small download, and very handy. (Link in my sig) Worth keeping on hand just in case.

---

