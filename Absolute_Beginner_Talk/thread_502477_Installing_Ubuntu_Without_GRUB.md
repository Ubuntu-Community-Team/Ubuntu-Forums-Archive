---
title: "Installing Ubuntu Without GRUB?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-07-16
Well, for some reason or another, I need to reinstall Ubuntu.  But, I already have GRUB installed, and that is working perfectly.  So, is it possible to install Ubuntu without also installing GRUB?

Thanks.

---

### Post by wolfen69 on 2007-07-16
it should see that grub is already installed and not be a problem.

---

### Post by Yes on 2007-07-16
Ah, ok.

Thanks.

---

### Post by theDaveTheRave on 2007-07-16
If you don't want to have to wait for the GRUB to do it's stuff and jump straight into Ubuntu you can edit the grub file and either reduce the delay for the boot into Linux, or remove the other boot options.

it all sits in the folder /boot/grub/  and the file <menu.lst> has the boot options.

Dave

---

