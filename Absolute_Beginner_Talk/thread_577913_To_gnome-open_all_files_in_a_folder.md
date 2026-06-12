---
title: "To gnome-open all files in a folder"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-16
How can I gnome-open all files in a folder?
I tried gnome-open ./* but does not work.

---

### Post by Billy_McBong on 2007-10-16
[COLOR="Blue"]in nautilus highlight all of them and hit enter[/COLOR]

---

### Post by Fixman on 2007-10-16
> **Billy_McBong said:**
> [COLOR="Blue"]in nautilus highlight all of them and hit enter[/COLOR]

Are you lolling me or something? I want an automated script for that, so it executes when I open the computer

---

### Post by Fixman on 2007-10-17
dude, is there a way?

---

### Post by Gwasanaethau on 2007-10-17
You could do:
```
for file in *; do
gnome-open "$file"
done
```
Be careful, because if you have more than a couple of files/directories in the current folder, it might turn your desktop into a mess of objects; possibly causing a crash if you have loads of items!

---

### Post by Fixman on 2007-10-19
> **Gwasanaethau said:**
> You could do:
```
for file in *; do
gnome-open "$file"
done
```
Be careful, because if you have more than a couple of files/directories in the current folder, it might turn your desktop into a mess of objects; possibly causing a crash if you have loads of items!

Thanks a lot, you really saved my hole life.

---

### Post by earobinson on 2007-10-19
hole = whole?

---

### Post by Gwasanaethau on 2007-10-20
You're welcome! ;)

---

### Post by Dr Small on 2007-10-20
> **earobinson said:**
> hole = whole?
Lol. Maybe he's a mole that lives in a "hole" :D

---

### Post by dfreer on 2007-10-20
I'm just curious, why would you want to open all the files in a folder anyways?

---

### Post by Fixman on 2007-10-21
> **dfreer said:**
> I'm just curious, why would you want to open all the files in a folder anyways?

I want to have a folder with all torrents Im downloading, so, when I turn on the computer, it automatically keep downloading files from before.

---

