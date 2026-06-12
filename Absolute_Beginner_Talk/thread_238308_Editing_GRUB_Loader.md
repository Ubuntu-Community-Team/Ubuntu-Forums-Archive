---
title: "Editing GRUB Loader"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Buildscharacter on 2006-08-17
I'm fairly new to the whole Linux thing and I was trying to figure out how to edit the GRUB loader. I found the files in the /boot directory, but when I go into them to change it, it tells me that I don't have permission to do so. I assume that I need to access the directory via the terminal and use a sudo command, but I can't figure out how to do it. Thanks.

---

### Post by coolclassic on 2006-08-17
To edit your grub file:

sudo gedit /boot/grub/menu.lst
password

You can now edit freely

---

### Post by Buildscharacter on 2006-08-17
Thanks. Knew it would be something simple.

---

### Post by nickpaton on 2006-08-17
Try GrubEd:

[http://www.ubuntuforums.org/showthread.php?t=228104]("http://www.ubuntuforums.org/showthread.php?t=228104")

A convenient GUI based GRUB editor.

Thanks to Tomosaur

---

### Post by anaconda on 2006-08-17
Or if you prefer graphical tools you can write

gksudo nautilus

to the terminal... This opens "file browser" with root (admin) rights, and when you open a file from it you have editing rights.

---

### Post by Buildscharacter on 2006-08-17
Thanks. I'll give it a try when I get home. Damn work won't let me install Ubuntu on my laptop...oh well. :D 

Thanks for the help.

---

