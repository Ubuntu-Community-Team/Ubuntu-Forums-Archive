---
title: "Two easy questions!"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by flaran on 2006-05-24
1. How do I replace my xorg.conf directly if I have a section of copied text?


2. What is HAL?

THANKS for any and all replies!

---

### Post by aysiu on 2006-05-24
[QUOTE=flaran]1. How do I replace my xorg.conf directly if I have a section of copied text?[/quote] What do you mean by *directly*? Can you even log in graphically? If so, you can use a text editor to paste the text in: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf
``` in Gnome or ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
kdesu kwrite /etc/X11/xorg.conf
``` in KDE.

I don't know if you can paste it in otherwise. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

> 
2. What is HAL?

THANKS for any and all replies! I believe it stands for Hardware Abstraction Layer and has something to do with automounting of external media.

---

### Post by dmizer on 2006-05-24
to paste into nano, highlight text to be copied ... hover over your nano with the mouse and middle click your mouse.  if you do not have three mouse buttons (or a scroll wheel button) you can emulate 3 buttons by clicking both left and right mouse buttons at the same time.

this method works in any application ... as long as you have a mouse.

---

### Post by dmizer on 2006-05-24
to insert text into nano with no mouse ... you can use the ctrl+R function.

to make this work, you will need the text you want in your xorg.conf saved in another file.  then, open nano and hit ctrl+R it will ask you what file you would like to insert from ... type the full path to the file (eg /home/dmizer/test.txt) and hit enter.  everything from the test.txt file will show up in xorg.conf now.

found that in nano's help file ... ctrl+g

---

