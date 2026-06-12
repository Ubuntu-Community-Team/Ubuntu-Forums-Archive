---
title: "Missing Desktop.ini for KDE Trashcan"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-03-15
I accidentally deleted my Desktop.ini file for my Trash Can/Waste Basket.

It's supposed to be located in /home/arthur/.local/share/Trash/files/Desktop.ini

The only way I have been able to delete my trash is through terminal

> 
$ xhost +
$ login as root (via 'su')
# konqueror &


When konqueror opens, I point it to trash:/ and just delete the trash from there.

Anyone know how to restore the .ini file?

---

### Post by shareMenaPeace on 2007-03-15
Did you searche dfor the file with eg:

```
locate filename
```

or

```
whereis filename
```

Maybe there is another one?

---

### Post by chavo on 2007-03-15
That's odd I don't have that file either and my trash:/ works fine.

---

### Post by lazyrussian on 2007-03-15
ok thanks sharmenapeace! I figured it out after using locate

I was quite curious why linux was looking for a desktop.ini file (I thought.ini was windows only)

Anyway, I realzied how I ended up int he predicament in the first place and everything is back to normal.

---

