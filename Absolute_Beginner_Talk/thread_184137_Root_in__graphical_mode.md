---
title: "Root in  graphical mode"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-29
In gnome we use:

"gksudo nautilus"     to enter root in graphical mode.

What is it in KDE? 
I have Kubuntu and would like to move about a few files without using the command line!

Thanks in advance for any suggestions

---

### Post by meng on 2006-05-29
Warning: I don't use KDE, therefore I might be leading you astray here:
Try:
kdesu konqueror

At least it shouldn't break your system. :)

---

### Post by hotbrainz on 2006-05-29
cheers mate..

worth a try i hope :)

---

### Post by catlett on 2006-05-29
It may be ```
kdesudo konqueror
``` It is  kdesu konqueror on systems that don't use sudo. So if kdesu doesn't work try kdesudo. I'm in gnome sorry I can't confirm.

---

### Post by Jucato on 2006-05-29
it's definitely
```
kdesu whatever_app
```
works not just for konqueror, but for everything else.

I'm a KDE user, so I know that works. :D

---

