---
title: "Installing XP on Vista/Ubuntu Dual-Boot Machine"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by navraj on 2008-03-21
I have a Vista/Ubuntu dual-boot on my machine. Now I would like to create another partition and install XP on it. The question is - what is the best way to handle bootloader issues? Will GRUB automatically detect the XP partition (I'm thinking its unlikely...). If not, what's the best way to go about doing this, and making sure I get a bootloader menu that lets me select ubuntu/vista/xp?

Thanks!

---

### Post by nick_h on 2008-03-21
Install XP, then re-install grub.

[How to install Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351)

Then edit your /boot/grub/menu.lst and add your XP partition.

Here is a link to the [grub manual](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows).

---

### Post by DSn0wMan on 2008-03-21
The probem isn't going to be with grub not seeing XP, but with XP wiping out grub.

---

### Post by madjr on 2008-03-21
> **navraj said:**
> I have a Vista/Ubuntu dual-boot on my machine. Now I would like to create another partition and install XP on it. The question is - what is the best way to handle bootloader issues? Will GRUB automatically detect the XP partition (I'm thinking its unlikely...). If not, what's the best way to go about doing this, and making sure I get a bootloader menu that lets me select ubuntu/vista/xp?

Thanks!

XP will wipe out grub.

so to restore it use **wingrub** (download it in win xp):

[http://sourceforge.net/projects/grub4dos](http://sourceforge.net/projects/grub4dos)

---

### Post by navraj on 2008-03-21
Thanks for the links, this is exactly what I was looking for. Hopefully this will work.

---

