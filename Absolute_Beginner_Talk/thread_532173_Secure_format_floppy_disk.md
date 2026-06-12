---
title: "Secure format floppy disk"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-08-22
Is this possible?

---

### Post by kidcharles on 2007-08-22
Could you clarify your question? You just want to format a floppy disk? What do you mean by "secure?"

---

### Post by alienexplorers on 2007-08-22
You can format a floppy in DOS or EXT2 format.  Never heard of a secure disk unless you move the slider on the disk to make it read only.

---

### Post by arijarot on 2007-08-22
I would like to erase/format a floppy disk in the same way that I would "shred" /dev/hda.

---

### Post by asmoore82 on 2007-08-22
you are more or less wasting your time when you "shred" a drive unless you are Physically shredding it :p

but the dd command in combo with sepcial devices will let you [re]write zeros
and random junk until you are blue in the face ...

```
~ $ dd if=/dev/zero of=/dev/fd0
~ $ dd if=/dev/random of=/dev/fd0
```

:KS lather, rinse, repeat \\:D/

---

### Post by arijarot on 2007-08-22
Thanks:)

---

### Post by irish_flu on 2007-08-22
I used to have a nice pair of scissors that were great for making sure the data on a floppy was gone  :KS

---

### Post by arijarot on 2007-08-22
I decided to use an actual shredder 8-)

---

### Post by kidcharles on 2007-08-22
Given my experience with floppies, it's only a matter of time before they are unreadable anyway.

---

### Post by arijarot on 2007-08-22
Very true. my laptop can't read them, but my desktop from 2002 can...

---

