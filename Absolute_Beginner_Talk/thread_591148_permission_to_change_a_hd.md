---
title: "permission to change a hd?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-25
hi there,

 i want to change a hard drive to read and write? when i try to do this through computer and right click it wont allow me.
do i need to login as root?

cheers,
stfury

---

### Post by taurus on 2007-10-25
What filesystem is that harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by stfury on 2007-10-26
its fat32 (an ipod)

---

### Post by Qwerty_ on 2007-10-26
Well if you want to learn about file permissions have a read here 

[https://help.ubuntu.com/community/FilePermissions#head-38812bb796d7900bb1a5fb5f369392f5a21b0f0b](https://help.ubuntu.com/community/FilePermissions#head-38812bb796d7900bb1a5fb5f369392f5a21b0f0b)


Otherwise 
I would just run nautilus in root to change the permissions.

```
sudo nautilus
```

---

