---
title: "[SOLVED] what graphics card do I have?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by ginestre on 2008-01-04
Is there some way to discover what graphics card I have -and consequently what modes it supports - without opening up the box?

---

### Post by Irony on 2008-01-04
```
lspci
```

---

### Post by ginestre on 2008-01-04
Thanks!

---

### Post by PeterJS on 2008-01-04
lspic is going to tell you everything that's on your system. To find just the graphics card try:
```

lspci | grep -i vga

```

---

### Post by Irony on 2008-01-04
Also;

```
System > Preferences > Hardware Information
```

---

