---
title: "How to save in terminal"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by DapperMe17 on 2006-12-01
Xubuntu Edgy 6.10


I've installed the Nvidia-legacy-glx video drivers & am trying to change "nv" to "nvidia" in xorg.

How do I actaully save that change in terminal, prior to restarting xorg?

Thanks!

---

### Post by cronholio on 2006-12-01
If you don't know vi, use nano to edit the file:

> sudo nano /etc/X11/xorg.conf

Keyboard shortcuts are displayed at the bottom of the screen (Ctrl+*).

---

### Post by DapperMe17 on 2006-12-01
I'm sorry, I don't understand. I'm new to Xubuntu.

I see a variety of commands, but nothing related to save. 

Can you tell me how to save my edited information in nano?

---

### Post by CatKiller on 2006-12-01
Ctrl-X exits, and asks if you want to save.

Ctrl-O saves, and asks what you want to save it as.

---

### Post by DapperMe17 on 2006-12-01
Figured it out.

Thanks

---

### Post by xyz on 2006-12-01
Hi and Welcome to Ubuntu:
Hold down the "Ctrl" key and then "X" on your keyboard, then press "y" for save changes.
Also:
[Nano Doc]("http://www.nano-editor.org/docs.php")
Also in a terminal:
```
man nano
```
Hope it helps! Feel free to ask more questions.

---

### Post by stream303 on 2006-12-01
One nano editor tip for down the road when editing system files:

use nano -w <filename> so that nano doesn't wrap long lines.

---

