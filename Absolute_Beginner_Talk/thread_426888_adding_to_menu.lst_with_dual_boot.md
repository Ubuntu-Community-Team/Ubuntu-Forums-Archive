---
title: "adding to menu.lst with dual boot"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kcbear on 2007-04-28
Hi,

New to Linux. am setting up a dual boot system, linux as master, windows as slave. Have read that you need to add some lines to Menu.lst so that you can choose which os to load. Tried to do this, however it says im not the owner and it wont let me change it or change the permissions.
any advice?

---

### Post by taurus on 2007-04-28
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Use the same password that you use to log in with your account.

---

### Post by dreadlord_chris on 2007-04-29
> **kcbear said:**
> Hi,

New to Linux. am setting up a dual boot system, linux as master, windows as slave. Have read that you need to add some lines to Menu.lst so that you can choose which os to load. Tried to do this, however it says im not the owner and it wont let me change it or change the permissions.
any advice?

Install Windows first then Ubuntu - the Ubuntu installer will configure menu.lst for dual-boot for you.

---

