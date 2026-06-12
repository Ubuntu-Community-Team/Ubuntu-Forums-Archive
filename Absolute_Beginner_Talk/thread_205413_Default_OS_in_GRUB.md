---
title: "Default OS in GRUB"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by veagles on 2006-06-28
When I start my computer, GRUB 0.97 comes up and boots my comp into Ubuntu. How do I make it boot XP by default?

---

### Post by aysiu on 2006-06-28
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by mmathiou on 2006-06-28
go to /boot/grub and edit the file "menu.lst". Inside the file there is an line:
# array will desync and will not let you boot your system.
default	        6	 
n order to boot in Windows my value is set to 6 because i have : 1)Ubuntu, kernel 2.6.15-25-386 2)Ubuntu, kernel 2.6.15-25-386 (recovery mode) 3) Ubuntu, kernel 2.6.15-23-386 4) Ubuntu, kernel 2.6.15-23-386 (recovery mode) 5)MemeTest 86+ 6) Windows XP

---

### Post by njzillest on 2006-06-28
you can also rename your the OS over there

---

