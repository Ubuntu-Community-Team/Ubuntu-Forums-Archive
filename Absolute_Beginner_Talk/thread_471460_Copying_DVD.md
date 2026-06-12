---
title: "Copying DVD"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-12
how does one copy a DVD to another ?in short is there a nero equivalent in ubuntu??

---

### Post by zvacet on 2007-06-12
**K3b**.It is in synaptic.

---

### Post by Bachstelze on 2007-06-12
```
dd if=/dev/whatever of=image.iso
```

Will create an image of the disk. You can then burn it using your favourite burning program.

---

