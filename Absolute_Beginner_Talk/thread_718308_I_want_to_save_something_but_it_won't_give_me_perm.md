---
title: "I want to save something but it won't give me permission"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by stropyboy11 on 2008-03-08
I want to save something in a certain folder, but it won't give me permission. How do I save something as root?

-Stropko

---

### Post by chewearn on 2008-03-08
What directory you are trying, and what application you are using?

---

### Post by stropyboy11 on 2008-03-08
I am trying to save a size 48x48 to /usr/share/icons/hicolor/48x48/apps/

long story why...and I'm just using the default ubuntu file manager...

---

### Post by Ecclesia on 2008-03-08
The easy way would be to run Nautilus as root by opening the terminal and typing "sudo nautilus".  Anything you do with it will be as root, so be really careful.

The safer way would be to move things around using sudo with terminal commands.

---

### Post by Shazaam on 2008-03-08
Be VERY careful with this code as it will open nautilus with FULL root permissions. Anything you do while using it is PERMANENT!
```
gksudo nautilus
```
Drag the file to the folder.

---

### Post by ph1 on 2008-03-08
If you're a little leery of gksudo nautilus just use a terminal, and type "sudo mv <file you want to move> <folder you want to move it to>".  It'll automatically overwrite anything that shares its name in the destination, though.

---

