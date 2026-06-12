---
title: "Will Ubuntu rewrite my GRUB?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by willywilly on 2006-08-16
I've got a fine working copy of GRUB on my system. Will a installation of Ubuntu break it and replace it with its own?

My GRUB is set up to launch Windows off hda1 and Linux off hda2. Ubuntu will work with this setting and I don't want to risk the installation process to destroy my GRUB.

Thanks a lot for your help. :)

---

### Post by Jagot on 2006-08-16
If you run the installation from the Desktop (live) CD then I think GRUB gets installed by default and will thus overwrite your current setup.  However, if you install from the Alternate Install CD then you have the option not to install GRUB, so you can keep your current settings.

---

### Post by willywilly on 2006-08-16
Great, thanks a lot.

---

### Post by daou on 2006-08-16
You can always backup your /boot/grub/menu.lst file. That contains all the information GRUB needs to boot your operating systems. If it gets rewritten, just replace the menu.lst with your backed up one.

---

