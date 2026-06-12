---
title: "mount point and editing my fstab"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-10-29
i need help!!! I need help doing both of those

---

### Post by Crafty Kisses on 2007-10-29
> **LiNuXxToOthEMaX said:**
> i need help!!! I need help doing both of those

To create a mount point do the following:
```
sudo mkdir /storage
```

Not sure what part you're at, but usually if you want to edit you fstab, it would go a little something like this:
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
Hope this helps. :)

---

### Post by taurus on 2007-10-29
What partition do you want to mount and where do you want to mount to?  You need to provide a little more info before anybody can help you.  If you are not sure which partition(s), post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by LiNuXxToOthEMaX on 2007-10-29
for some reason i did those commands, and it like didn't like go through for example it didnt like see that i made changes. any ideas?

---

### Post by Crafty Kisses on 2007-10-29
> **LiNuXxToOthEMaX said:**
> for some reason i did those commands, and it like didn't like go through for example it didnt like see that i made changes. any ideas?

Try this:
```
sudo mount -a
```

---

### Post by Crafty Kisses on 2007-10-29
> **LiNuXxToOthEMaX said:**
> for some reason i did those commands, and it like didn't like go through for example it didnt like see that i made changes. any ideas?

Did that work?

---

