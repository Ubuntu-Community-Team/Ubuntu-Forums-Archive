---
title: "Memory Space"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Shichao on 2007-12-13
My disk usage analyzer says I have 5.4 GB of free space, but when I try to download a 3611 MB file it says there's not enough space.             :confused:

---

### Post by taurus on 2007-12-13
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by fmartinez on 2007-12-13
It's probably using the remaning space as SWAP.......

---

### Post by Shichao on 2007-12-14
> **taurus said:**
> Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```


when i did that it says i only have 1.9 GB free space?

---

### Post by SOULRiDER on 2007-12-14
Maybe what youre using to show space is counting the usaed space in your trash as free. Try empying it. Alos, you can use a program like Filelight (its for KDE, i dotn know any such programs for GNOME) to see where all your space is going.

---

