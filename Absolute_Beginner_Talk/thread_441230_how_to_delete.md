---
title: "how to delete"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-05-12
how to delete this from desktop. 

/home/ohm/Desktop/jre1.6.0_01

If I do it says I do not have permission. dual boat single user

---

### Post by Kobalt on 2007-05-12
```
sudo rm /home/ohm/Desktop/jre1.6.0_01
```

---

### Post by earobinson on 2007-05-12
> **Kobalt said:**
> ```
sudo rm /home/ohm/Desktop/jre1.6.0_01
```
That will do it. always be cairful with rm since you wont be able to get the files back (they are removed not put in the trashcan)

---

### Post by drpas2k on 2007-05-12
i tried all these, but failed

rm: cannot remove `/home/ohm/Desktop/jre1.6.0_01': Is a directory
ohm@ohm-desktop:~$ sudo rmdr /home/ohm/Desktop/jre1.6.0_01
sudo: rmdr: command not found
ohm@ohm-desktop:~$ sudo rmdir /home/ohm/Desktop/jre1.6.0_01
rmdir: /home/ohm/Desktop/jre1.6.0_01: Directory not empty

---

### Post by jfinkels on 2007-05-12
```
sudo rm -r /home/ohm/Desktop/jre1.6.0_01
```

The -r option tells the rm program to recursively visit every file included within the directory and delete it, THEN delete the directory that contained those files.

---

### Post by stalker145 on 2007-05-12
> **drpas2k said:**
> how to delete this from desktop. 

/home/ohm/Desktop/jre1.6.0_01

If I do it says I do not have permission. dual boat single user

You can also **gksudo nautilus** (or your file manager of choice) and delete it that way if you like the GUI. I use both, but the GUI gives me a warm and fuzzy.

EDIT: Fixed to read gksudo on advice listed below.

---

### Post by jiminycricket on 2007-05-12
be careful to use gksudo instead of just sudo with graphical apps like nautilus

---

