---
title: "Removing GRUB but not Ubuntu"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by haseebanjum on 2007-12-27
Hi,
 Just installed Ubuntu! My first linux experience.
Ok, So I have XP and Ubuntu! But I don't like the default bootloader for ubuntu (the grub) i think. Can I remove GRUB ( I dont want to uninstall ubuntu) but use the windows bootloader for selecting my OS?

Didnt find much help on this on google, found this site ([http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)) but I cant use these commands (terminal says permision denied) besides I dont understand them.

Please help me
Thanks

---

### Post by jken146 on 2007-12-27
I had a quick glance at those instructions.  Perhaps you just need to use sudo ([https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)).  I would really recommend keeping GRUB though, because it is much more customisable than the Widows XP bootloader, it can be fixed from the live CD, and it will pick up the new options autmatically every time you do a kernel update (these come through maybe twice every 6 months).  If you do go with the Windows bootloader, don't forget to add an entry for Ubuntu's recovery mode!

Oh, and there is LILO too... you might want to look into that.

---

### Post by zero-9376 on 2007-12-27
if your worried about the way it looks yu might want to try gfxboot

---

