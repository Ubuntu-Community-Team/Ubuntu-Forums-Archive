---
title: "Dual booting Windows XP and ubuntu 7.10 (XP installed first)"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2008-02-05
I already have several systems running with ubuntu 7.10. I love ubuntu and I love linux, but, it is an unfortunite fact that computer games come out for windows, so i don't want to take xp off my gaming rig.

I recently however, thought of the possibility of dual booting xp and linux, but the guides i have checked out ([http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu) mainly), don't deal with 7.10. 

I also want to be **assured** of several things:
Not a single thing will be affected (other than the space clearly devoted to 7.10)
Not the network connection or anything. I have read too much about failed dual booting and a single os taking over, and i want to be able to continue gaming on my machine. I just want to be able to switch to ubuntu... In a sence, two different computers in one computer, linked by components and hard drives. I want to have to switch files between the two with a flash drive! I need to know that my current os is protected.

---

### Post by emarkd on 2008-02-05
There's no change in the installation procedure, so that guide will work fine.  If you install Ubuntu onto it's own partition, Windows will be unaffected and Grub will configure your computer for dual-booting.  But always make a backup.  Computers crash; people hit the wrong button; things go wrong.  Always back up.

---

### Post by Therion on 2008-02-05
> **Mitchlb said:**
> 
I also want to be **assured** of several things: ... 
Done correctly dual booting will do all those things.  I dual-booted for months before letting XP go by the wayside.  "Failed" installs, where the Windows partition gets wiped out, is usually due to Operator Error.  A clean dual-boot setup really is the best of both worlds.  Your XP install will be just as it was and you can boot back into it any time you want with no more than a keystroke at the GRUB menu.

---

### Post by mikewhatever on 2008-02-05
7.10 has ntfs-3g, the driver for write access to ntfs, installed by default. That means you'd be able to delete any file on your Windows partition while running Ubuntu. The way to deal with it is not to mount Windows, or to uninstall ntfs-3g. I've chosen the first way to protect both ntfs and fat32 (recovery partition) by commenting them out in /etc/fstab. It would still be possible to mount ntfs manually, and I could not find the way to disable that.
You could also create an NTFS/FAT32 storage partition aimed to be accessible to both Windows and Ubuntu instead of using a flash drive.

---

### Post by tanman on 2008-02-05
Here is a video on installing Ubuntu and a dual boot.
[Install video]("http://www.msccompcasts.com/2006/11/install-videos-of-ubuntu-ubuntu-install.html")
Also check this Podcast episode out
[MSC Giz Cast Video Episode]("http://www.msccompcasts.com/2006/11/install-videos-of-ubuntu-ubuntu-install.html")

---

