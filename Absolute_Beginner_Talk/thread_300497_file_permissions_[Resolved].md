---
title: "file permissions [Resolved]"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by VirginGeek on 2006-11-15
I have been using Ubuntu for only a week and love it even though it is a challenge. The problem I'm having is that I'm trying to change the menu.lst file in the boot/grub folder. My objective is to change the default boot OS but it tells me that root is the owner of the read only file and it cannot be changed. I do have admin rights on the machine and when I log in as root, it tells me that admins shouldn't log in this way on the login screen. ](*,) ](*,) Help please.

---

### Post by mitch.c on 2006-11-15
> **VirginGeek said:**
> I have been using Ubuntu for only a week and love it even though it is a challenge. The problem I'm having is that I'm trying to change the menu.lst file in the boot/grub folder. My objective is to change the default boot OS but it tells me that root is the owner of the read only file and it cannot be changed. I do have admin rights on the machine and when I log in as root, it tells me that admins shouldn't log in this way on the login screen. ](*,) ](*,) Help please.
See this link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The root account is disabled by default. Ubuntu is setup to use sudo for admin tasks. What you want to do is:
```
$ sudo gedit /boot/grub/menu.lst
```

---

### Post by aysiu on 2006-11-15
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by VirginGeek on 2006-11-16
Fixed!!:p Thanks for the help Guys. Till next time

---

