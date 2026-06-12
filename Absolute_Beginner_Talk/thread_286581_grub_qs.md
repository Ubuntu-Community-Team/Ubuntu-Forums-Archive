---
title: "grub qs"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by thor908 on 2006-10-27
How do I trap the grub and see the scripts in the menu to see what parameters it uses during boot-up

im booting from my external hard drive and all i get is 
/bin/sh: cant access tty; job control off

does this mean anything to any one?

---

### Post by kvonb on 2006-10-28
Try hitting the ESC key as it boots, then 'e' to edit the command line, then 'b' to boot.

Alternatively, boot from the Ubuntu CD, then edit the menu.lst on your external HDD (I believe you will have to mount it first).

sudo gedit /mount-point/wherever-you-mounted-it/boot/grub/menu.lst

---

