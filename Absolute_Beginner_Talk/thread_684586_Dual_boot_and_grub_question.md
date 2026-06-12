---
title: "Dual boot and grub question"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2008-02-01
I presently have a 250Gb Sata hard drive with Gusty installed on it, But I would like to add a second drive, an IDE drive, and install Windoze XP on it so I can play a few windoze games and use Photoshop and Dreamweaver etc.

How can I do this without re-installing Gusty so I can choose which OS to boot to in the GRUB screen??

---

### Post by iris-n on 2008-02-01
It's hard, since windows tend to overwrite grub and ignore the ubuntu existence. But, you can boot from a live CD and reinstall grub, in [their]("http://www.gnu.org/software/grub/manual/grub.txt") page they teach several ways of reinstalling it. I already did it once, but for a debian overwrite, not a windows one.

---

### Post by kellemes on 2008-02-01
Just install Windows and let it do it's thing..
Use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") (download/burn/boot) to reinstall Grub from your Linux-install. Then you simply add an entry for Windows in your /boot/grub/menu.lst

Edit: Always assume things to go wrong.. so backup important stuff to be safe.

---

### Post by ianb72 on 2008-02-01
> **kellemes said:**
> Just install Windows and let it do it's thing..
Use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") (download/burn/boot) to reinstall Grub from your Linux-install. Then you simply add an entry for Windows in your /boot/grub/menu.lst

Edit: Always assume things to go wrong.. so backup important stuff to be safe.

Thanks 
I'll give that a go.

Ian

---

