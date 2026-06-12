---
title: "setting permissions"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2006-12-16
I am wondering how to set permissions b/c I cant create a new folder w/out going into the terminal

Can anyone help me??

---

### Post by patrick.dylan on 2006-12-16
Right-click > Properties > Permissions  (in a folder window)
"chmod" at the command line.

---

### Post by RED WIND on 2006-12-16
cant im not root

---

### Post by taurus on 2006-12-16
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by RED WIND on 2006-12-16
i found it

I used sudo -i

---

### Post by patrick.dylan on 2006-12-16
> **RED WIND said:**
> i found it

I used sudo -i

Careful... then you're operating as root. It's safer (an encouraged) to use sudo for each root level command instead.

```
sudo *command*
```

---

