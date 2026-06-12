---
title: "computer/trash icon on desktop"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by yuvlevental on 2007-07-10
how do i get the computer/trash icon t how on desktop?

---

### Post by tak1150 on 2007-07-10
In a terminal, 
```
gconf-editor
```

Then go to apps --> nautilus --> desktop,
you should find a section about showing trash icon on the desktop and check it.

---

### Post by fastpakr on 2007-07-10
Sorry for the hijack, but I've got a related question.  I've got multiple partitions - how do I create trash icons for those, rather than having to go to the .Trash-user folder to manually clear them?

---

### Post by alienexplorers on 2007-07-10
I have multiple partitions and only one trash icon.  All you should have is one icon.

---

### Post by tak1150 on 2007-07-10
> **fastpakr said:**
> Sorry for the hijack, but I've got a related question.  I've got multiple partitions - how do I create trash icons for those, rather than having to go to the .Trash-user folder to manually clear them?

How are they mounted?
Whether you have a unified trash icon or not depends on the way they are mounted.

---

### Post by fastpakr on 2007-07-10
They're mounted in fstab based on the UUID - does that answer the question?  I only have one icon, but it refers to the SATA drive that Ubuntu is being run from.  I've got two other PATA drives in ext3 format that are a pain to manage deleted files on.

---

