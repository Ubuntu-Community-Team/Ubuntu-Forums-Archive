---
title: "Boot screen change"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Windoze Convert on 2006-11-17
My boot screen changed from the awesome Ubuntu to an edubuntu which I don't like.  I don't remember just hat I did to change it and need some help to get the original back.

---

### Post by 56phil on 2006-11-17
Did you change /boot/grub/menu.lst?

---

### Post by DigitalAxis on 2006-11-17
The GRUB configuration merely tells the kernel to boot WITH usplash; it doesn't specify WHICH usplash.

To Windoze Convert:  Try running **sudo dpkg-reconfigure usplash-theme-ubuntu**

or if that fails, **sudo aptitude reinstall usplash-theme-ubuntu**


[EDIT] If anyone knows a method that doesn't involve the command line, please let me know

---

