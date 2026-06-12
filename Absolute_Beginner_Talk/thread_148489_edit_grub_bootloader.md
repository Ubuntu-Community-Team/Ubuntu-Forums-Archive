---
title: "edit grub bootloader"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by big-hed on 2006-03-22
I want to edit my grub bootloader so that ubuntu is the dafault OS to boot and not Windows..????

I have used Fedora Core distros before and you could edit the bootloader options from within the desktop , HOW CAN THIS BE DONE IN UBUNTU???

:confused: :confused: :confused: :confused:

---

### Post by chuckyp on 2006-03-22
You have to edit the file /boot/grub/menu.1st

---

### Post by kenweill on 2006-03-22
Open a Terminal Window.
type
sudo gedit /boot/grub/menu.lst

---

### Post by PhilOSparta on 2006-03-22
This location will give you the specifics.

[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

---

