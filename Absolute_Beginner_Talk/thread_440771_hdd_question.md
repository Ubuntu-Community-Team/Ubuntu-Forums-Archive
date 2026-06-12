---
title: "hdd question"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2007-05-11
ok
i have ubutu on a small hdd and i have a slave hdd in and it shows up on the destop when i got to put stuff in it it says "you do not have permision to do this" i dont know what that means if some on e could help that would be great

thanks

---

### Post by taurus on 2007-05-11
What filesystem is that slave drive?  If you need to write to it, try using nautilus as root.

<Alt>F2 -> gksudo nautilus

---

### Post by yimmmy on 2007-05-11
i pressed that button and nuthing happend im not sure what to do i really need this drive

---

### Post by taurus on 2007-05-11
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

Again, what filesystem is that drive?

```
sudo fdisk -l
```

---

### Post by yimmmy on 2007-05-11
i dont know how and what those codes are 
and the file system do u mean like fatx or somthing like that 
i think is nts

---

