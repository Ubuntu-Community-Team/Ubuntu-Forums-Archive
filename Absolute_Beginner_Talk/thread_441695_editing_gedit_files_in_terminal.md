---
title: "editing gedit files in terminal"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-05-12
hello
i have a graphic environment problem that doesn't allow me to use gedit because.. I don't have a graphic environment!
how can I edit a gedit file such as /etc/x11/xorg.conf in the terminal without using sudo gedit?
is there a line of command that allows you to open this kind of files actually IN the terminal?

---

### Post by wormser on 2007-05-12
try

**sudo nano file**

or 

**sudo vi file**

---

### Post by taurus on 2007-05-12
```
sudo nano -Bw /etc/**X**11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to edit.

---

### Post by Morkhaar on 2007-05-12
thanks a lot! :)

---

