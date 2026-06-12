---
title: "how to delete locked folders"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by bravo26 on 2007-05-02
I was transfering some files to my computer from a friends external hd, and the drive became unplugged causing a couple folders to be not fully transfered.  I want to delete them but they have a little lock icon on them and i get the message "Cannot move "/home/scott...top/Raptor" to the trash because you do not have permissions to change it or its parent folder." and I can't drag and drop them to the trash either....any way to unlock these folders?  Thanks

---

### Post by [S|G] on 2007-05-02
Try to open a terminal and type this:
```
sudo rm -Rf /home/scott...top/Raptor
```
This should remove the folder permanently.

---

### Post by taurus on 2007-05-02
Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Now, delete them as root.

---

### Post by firedragonsf on 2007-12-09
> **'[S|G] said:**
> Try to open a terminal and type this:
```
sudo rm -Rf /home/scott...top/Raptor
```
This should remove the folder permanently.


this worked thx

---

