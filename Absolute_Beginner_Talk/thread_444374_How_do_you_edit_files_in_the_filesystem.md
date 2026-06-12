---
title: "How do you edit files in the filesystem?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by the.dark.lord on 2007-05-15
Title says all. It says the owner is *root* and I can't change the permissions. What should I do to edit the files in the filesystem? Thanks.

---

### Post by taurus on 2007-05-15
Applications -> Accessories -> Terminal
```
gksudo gedit **filename**
```

---

### Post by Dr Small on 2007-05-15
or
```
gksudo nautilus
```
and browse the file system in nautilus as root, or
```
sudo pico /path/to/file/name.txt
```

Dr Small

---

### Post by rich.bradshaw on 2007-05-15
If you want to edit them, you have to switch user to root, using sudo. This lets you perform a command as root.

---

### Post by the.dark.lord on 2007-05-15
Hey guys, I found out the answer. 

Go to the terminal and type 

gksudo nautilus

EDIT: Thanks for answering all. This sure is an active forum ;)

---

