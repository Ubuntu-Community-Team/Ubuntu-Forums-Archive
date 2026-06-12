---
title: "Can't Edit sources.list file"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2006-04-21
I need help figuring out how to edit my sources.list file. It will only open as 'read only'. and i can't seem to get the priveleges to edit this. what am I missing?

---

### Post by pbaehr on 2006-04-21
You need to use sudo to give yourself superuser priveledges.

If you're using Gnome: open up a terminal window and type:
```
sudo gedit /etc/apt/sources.list
```

This will work regardless of what you're using:
```
sudo nano /etc/apt/sources.list
```

---

### Post by manishsingh4u on 2006-04-21
[QUOTE=mlhudson]I need help figuring out how to edit my sources.list file. It will only open as 'read only'. and i can't seem to get the priveleges to edit this. what am I missing?[/QUOTE]

Run gnome-terminal and type
```

sudo gedit /etc/apt/sources.list

```
It will ask for password, give your own password.

---

### Post by mlhudson on 2006-04-21
You guys are incredible...3 minutes and i'm cruising! Thanks!:KS

---

