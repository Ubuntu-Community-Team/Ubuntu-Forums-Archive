---
title: "Remove kernel from bootup"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-02-10
I have just updated to kernel 2.6.15.28-386 and all works fine. I have 2 other kernels (2.6.15.23 and 2.6.15.27) which i am able to use, and what I want to do is remove the 2.6.15.23-386 kernel so i cannot login to it.

How do I do this?

Cheers

---

### Post by igknighted on 2007-02-10
> **spamzilla said:**
> I have just updated to kernel 2.6.15.28-386 and all works fine. I have 2 other kernels (2.6.15.23 and 2.6.15.27) which i am able to use, and what I want to do is remove the 2.6.15.23-386 kernel so i cannot login to it.

How do I do this?

Cheers

All you need to do to remove them from the grub menu is this:
```
gksudo gedit /boot/grub/menu.lst
```
^^^note, this is assuming you are using gnome, for KDE of Xfce use a text editor of your choice

This should ask you for your password, then open a text file.  If you scroll to the bottom you will find there will be sections that look like this:
```
[title Fedora Core (2.6.19-1.2895.fc6)
        root (hd1,0)
        kernel /boot/vmlinuz-2.6.19-1.2895.fc6 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.19-1.2895.fc6.img
```
but with your kernels on there.  What you need to do is put '#' characters before each line of the kernels that you don't want to show up on the GRUB menu.  Alternatively, you could just erase them, but its better to leave them just commented out in case they are needed later on (e.g., if you break you current kernel somehow).  Then save it and close the file, and it should be all set.

---

### Post by spamzilla on 2007-02-10
Excellent, thanks for that :)

---

### Post by Zyphrexi on 2007-02-12
/begin pirate_mode

arrr... couldn't ye remove them thar kernels usin apt? arrr

/end pirate_mode

---

