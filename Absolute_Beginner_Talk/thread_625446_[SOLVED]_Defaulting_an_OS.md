---
title: "[SOLVED] Defaulting an OS"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by vbala757 on 2007-11-28
I have installed Ubuntu and am doing dual booting with Windows XP. At the boot selection screen it automatically defaults to Ubuntu. How do I default to windows instead of Ubuntu. Can any one help?

Bala

---

### Post by vbala757 on 2007-11-28
I have installed Ubuntu and am doing dual booting with Windows XP. At the boot selection screen I automatically default to Ubuntu. How do I default to windows instead of Ubuntu. Can any one help?

Bala

---

### Post by jr.gotti on 2007-11-28
Edit /boot/grub/menu.lst and change the "default" value.

---

### Post by x64Jimbo on 2007-11-28
Google "GRUB default OS"

---

### Post by aysiu on 2007-11-28
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by oeolycus on 2007-11-28
I can't find a handy guide, but follow jr.gotti's instructions and you should be fine.

Just count down the "titles" (starting with 0) until you hit Windows and change the default value to that number.

EDIT: here's that [handy guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu"), duh me.

---

### Post by Partyboi2 on 2007-11-28
Can you post your /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
then I can help you change it.

---

### Post by vbala757 on 2008-01-20
Many thanks to members who posted a reply to "Defaulting an OS". I have successfully defaulted to "Windows". Thanks again to those who responded.

Bala:)

---

