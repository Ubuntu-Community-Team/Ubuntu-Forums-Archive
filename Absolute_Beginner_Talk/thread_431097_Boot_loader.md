---
title: "Boot loader"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Jeff311 on 2007-05-02
Hi, I am brand new to Linux and the Ubuntu environment.  I was wondering if it was possible to change the boot loader (is it called GRUB?) that loads right after the post to have my Windows XP first on the list?

---

### Post by GrueTamer on 2007-05-02
> **Jeff311 said:**
> Hi, I am brand new to Linux and the Ubuntu environment.  I was wondering if it was possible to change the boot loader (is it called GRUB?) that loads right after the post to have my Windows XP first on the list?Sure, just go to the terminal and type

```
sudo gedit /boot/grub/menu.lst
```

And copy the entire Windows XP section, down at the very bottom, probably, and paste it on top of the Ubuntu entries.  You can even make a divider for yourself, much like the one separating Ubuntu and Windows by default.

You can also make Windows the default OS loaded if you want.  An easy way to do this is using the program [GrubEd]("http://ubuntuforums.org/showthread.php?t=228104").  Instructions are in the zip file.

---

### Post by Jeff311 on 2007-05-02
Thanks a lot!

---

