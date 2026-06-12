---
title: "Trying to format NTFS to ext3"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-10-29
It's just not working out, what do i need to use

---

### Post by Crafty Kisses on 2007-10-29
> **LiNuXxToOthEMaX said:**
> It's just not working out, what do i need to use

You probably want to use **gparted**:
```
 sudo apt-get install gparted
```

---

### Post by Crafty Kisses on 2007-10-29
Did that work?

---

### Post by LiNuXxToOthEMaX on 2007-10-29
> **Codename said:**
> Did that work?

ya how do i view the partition tho

---

### Post by bodhi.zazen on 2007-10-29
> **LiNuXxToOthEMaX said:**
> It's just not working out, what do i need to use

What is not working exactly ? What tool are you using and what error message or problem have you had ?

---

### Post by Crafty Kisses on 2007-10-29
> **LiNuXxToOthEMaX said:**
> ya how do i view the partition tho

You might want to try:
```
sudo fdisk -l
```

---

### Post by taurus on 2007-10-29
And before you can convert it from ntfs to ext3, you need to unmount it first if it's already mounted.  Can't format a mount partition.

---

