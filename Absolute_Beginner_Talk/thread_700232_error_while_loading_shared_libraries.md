---
title: "error while loading shared libraries"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-18
When opening a game via Terminal this error is shown:
> error while loading shared libraries: libgnomeui.so.32: cannot open shared object file: No such file or directory


What should I do now?

---

### Post by jan de beuker on 2008-02-18
Try installing it with the packet manager

---

### Post by adi_das on 2008-02-18
What file?

---

### Post by jan de beuker on 2008-02-18
The one you are missing

libgnomeui

---

### Post by adi_das on 2008-02-18
Same problem

---

### Post by jan de beuker on 2008-02-18
Type in a terminal

sudo ldconfig

---

