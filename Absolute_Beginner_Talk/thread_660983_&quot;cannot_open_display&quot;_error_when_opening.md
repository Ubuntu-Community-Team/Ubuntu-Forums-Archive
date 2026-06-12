---
title: "&quot;cannot open display:&quot; error when opening app from terminal"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by spydon on 2008-01-07
When I try to do for example:
```
sudo gedit vsftpd.conf
```
or
```
sudo mousepad vsfrpd.conf
```
or with all text editorors with GUI that I have tried I get:
(mousepad:7333): Gtk-WARNING **: cannot open display:  
leafpad: cannot open display: 
gedit: cannot open display:

Does anyone know how to fix it?

---

### Post by maruchan on 2008-01-07
I can't remember why that specific error, but use "gksudo" instead of "sudo" when you're running window system-based software from the command line. In KDE, use "kdesu".

---

### Post by spydon on 2008-01-07
> **maruchan said:**
> I can't remember why that specific error, but use "gksudo" instead of "sudo" when you're running window system-based software from the command line. In KDE, use "kdesu".

I get the same error with gksudo.

---

