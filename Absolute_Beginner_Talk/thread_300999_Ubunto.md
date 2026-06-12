---
title: "Ubunto"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Desy on 2006-11-16
Can anyone tell me how to access a file that has restrictions on it.  I am trying to edit /boot/grub/menu.lst so i can dual boot with another o/s but it wont let me save anything as i dont have permission.  Thanks

---

### Post by meng on 2006-11-16
sudo nano /boot/grub/menu.lst

The sudo gives you superuser privileges. Enter your user password when prompted.

---

### Post by earobinson on 2006-11-16
```
sudo <edit program> /boot/grub/menu.lst
``` In general sudo makes any following command be done as root. Also you may want to rename this thread, you will get more feedback that way. ```
man sudo
``` for more information

---

### Post by xpod on 2006-11-16
Even just a re-spelling would be a start;)

---

### Post by TheWizzard on 2006-11-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

