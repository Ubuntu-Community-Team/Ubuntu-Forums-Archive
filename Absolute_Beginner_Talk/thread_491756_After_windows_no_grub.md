---
title: "After windows no grub"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-07-04
I had to make a new partition and install windows on it because my internet service provider only supports windows and mac >_<

so now it goes to windows when booting and no more grub
how do I fix this?

---

### Post by logos34 on 2007-07-04
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by alienexplorers on 2007-07-04
Insert Live CD and boot.  Enter terminal and type sudo grub.
Enter:
> find /boot/grub/stage1

You will come up with a line such as (hd#,#)
Enter:
> root (hd#,#)
setup (hd#)
quit grub
reboot

---

### Post by Gmbrdilos on 2007-07-04
thanks guys, I will try it in a bit.

---

