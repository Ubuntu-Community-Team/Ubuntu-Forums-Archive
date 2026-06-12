---
title: "menu.lst?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by The Lawnmower on 2005-12-13
I am trying to configure GRUB for my dual boot system. Everything I've read says to edit 
/boot/grub/menu.lst
but I do not have such a file (or directory). In fact there is *nothing* in /boot.
I'm completely new to linux but this doesn't seem quite right to me.

A GRUB boot menu comes up when I boot the system, but how in god's name do I configure it?

---

### Post by 23meg on 2005-12-13
That's really weird. Which version of Ubuntu are you using? Can you see the files when you view the directory contents as root?

---

### Post by The Lawnmower on 2005-12-13
[QUOTE=23meg]That's really weird. Which version of Ubuntu are you using? Can you see the files when you view the directory contents as root?[/QUOTE]
BB 5.10.

As super user in terminal the ls command turns up nothing.

---

### Post by 23meg on 2005-12-13
Did this happen after a kernel update or dist-upgrade? Did you make any other major changes? What other directories do you see under / ?

---

### Post by kingsidy on 2006-01-12
start nautilus as root type in > gksu nautilus browse to your boot folder then grub and see if you see the menu.lst. it is quite odd that you cannot find it.

---

### Post by jonathanm on 2006-01-12
try:
sudo mount /boot
(if its in your fstab)

---

### Post by jorn on 2006-01-12
Does nothing show up when you type in terminal:
sudo gedit /boot/grub/menu.lst
Regards -Jorn

---

