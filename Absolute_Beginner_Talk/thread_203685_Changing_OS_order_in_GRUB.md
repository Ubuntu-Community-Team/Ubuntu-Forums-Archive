---
title: "Changing OS order in GRUB"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Groth on 2006-06-25
I would like to change the order of the operating systems listed in GRUB, since it annoys me to constantly have to move down to select the OS I want. Is it possible to do this? Thanks.

---

### Post by aysiu on 2006-06-25
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by nanotube on 2006-06-25
[QUOTE=Groth]I would like to change the order of the operating systems listed in GRUB, since it annoys me to constantly have to move down to select the OS I want. Is it possible to do this? Thanks.[/QUOTE]

yes it is. you should edit the file /boot/grub/menu.lst
you have two options:
1. move the entries around in the file
2. change which one is selected by default, without moving them around (there is a line at the beginning that looks like "default 0", and you can change the 0 to the number of the entry you would like to be selected by default [but note that the numbering starts at 0, not at 1.])

edit: ah, well, looks like aysiu already posted a more comprehensive link on this topic :).

---

