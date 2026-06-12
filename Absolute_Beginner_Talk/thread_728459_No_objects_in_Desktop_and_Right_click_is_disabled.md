---
title: "No objects in Desktop and Right click is disabled"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-18
There are No objects in Desktop and Right click is disabled. So I tried to paste a file in the Desktop and then also no file in Desktop. But I can see that file in the desktop in my home directory. I can right click anywhere except in the desktop.

---

### Post by glennric on 2008-03-18
Are you running compiz or metacity (i.e. Desktop Effects or not)?

---

### Post by adi_das on 2008-03-18
No desktop effects.

---

### Post by glennric on 2008-03-18
Ok.  Try running gconf-editor (type "gconf-editor" in a terminal), go to apps->nautilus->preferences and look for show_desktop.  Make sure that is checked.

---

### Post by adi_das on 2008-03-18
Yes it is checked. I already tried it.So i changed my file manager to thunar. I had this problem in Nautilu as well as Thunar.

---

