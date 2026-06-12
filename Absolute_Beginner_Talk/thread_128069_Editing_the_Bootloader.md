---
title: "Editing the Bootloader"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by thort on 2006-02-10
Hi !

Where in Ubuntu 5.10 do I edit the Bootloader? I've searched thru the applications but can't find it. I run Gnome.

---

### Post by Klaidas on 2006-02-10
You need to edit your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```

This guide is a howto about grub: [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)
Or, if you just want to change the default OS go straight here: [https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by thort on 2006-02-10
Thank You !

---

