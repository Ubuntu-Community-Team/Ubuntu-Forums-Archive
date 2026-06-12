---
title: "trash icon"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by raxx on 2007-12-11
Does anyone know anyway to show the trash can icon on the desktop in gnome? Thanks.

---

### Post by chips24 on 2007-12-11
i dont entirely know how, but you could install an icon theme and use that template to create youre own icons, i did that to change the buttons on my window border. try [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by RomeReactor on 2007-12-11
Hi. Open a terminal (Applications->Accessories->Terminal) and enter the following:
```
gconf-editor
```
In it, go to **apps->nautilus->desktop** and check the box **trash_icon_visible**.

---

### Post by Therion on 2007-12-11
Open the terminal:

```
gconf-editor
```

Navigate to apps->nautilus->desktop. 

Put a checkmark in the “trash_icon_visible” option.

---

### Post by fenian on 2007-12-11
nevermind

---

### Post by raxx on 2007-12-12
Nice! Thanks all.

---

### Post by Armanisc on 2007-12-13
Thanks for this

---

### Post by cbrigstocke on 2007-12-21
Thanks as well.

---

