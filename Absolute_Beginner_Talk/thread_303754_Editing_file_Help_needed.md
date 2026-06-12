---
title: "Editing file Help needed"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-20
I'm trying to edit my menu.slt file and save it. but the following error

"Could not save the file /boot/grub/menu.lst.
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

How do i set the premissions stuff to able to edit and save my files
Thanks in advance

---

### Post by glotz on 2006-11-20
You'll need to use sudo to be able to save that. e.g. 
sudo nano /boot/...
gksudo gedit /boot/...

---

### Post by jordanmthomas on 2006-11-20
run from a terminal (or from Alt + F2)
```
gksu gedit /path/to/file
```
This will allow you to edit the file with root privileges.


**edit, beaten, but not as much as some people :)

---

### Post by melancholeric on 2006-11-20
sudo gedit /boot/grub/menu.lst

edit: I'm way too slow for this forum.

---

### Post by ewl1217 on 2006-11-20
Press Alt+F2 and enter this command:
```
gksudo gedit /boot/grub/menu.lst
```
Just take extreme caution as it is an extremely important system file.

---

### Post by madmetal on 2006-11-20
open a terminal and write
sudo gedit /boot/grub/menu.lst

---

### Post by madmetal on 2006-11-20
wow! that means speed :)

---

### Post by kiyometane on 2006-11-20
Thanks guys

---

### Post by glotz on 2006-11-20
> **jordanmthomas said:**
> beaten, but not as much as some people :D

---

