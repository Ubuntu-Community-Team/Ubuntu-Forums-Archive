---
title: "[SOLVED] Move file in home/root that has spaces in the file name?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by neander on 2007-08-17
How can I move a file using cp which has spaces in the file name?

cp /dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816 /media/ubuntu

ubuntu 7.04 config 20070816         is the file name.

No file manager w/gui will allow me into home/root, but if there is a way to do that, it'd solve.

---

### Post by wormser on 2007-08-17
> **neander said:**
> How can I move a file using cp which has spaces in the file name?

cp /dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816 /media/ubuntu

ubuntu 7.04 config 20070816         is the file name.

No file manager w/gui will allow me into home/root, but if there is a way to do that, it'd solve.

Put a \ in front of the space.  Like this.

> ubuntu\ 7.04\ config\ 20070816

The other method is to open nautilus with gksudo for root privileges.

```
gksudo nautilus
```

Gksudo is like sudo but is used for gui apps.

---

### Post by schorsch on 2007-08-17
Just take a look in the other thread you started about this not long ago .. ;-)

[here]("http://ubuntuforums.org/showthread.php?t=528079")

---

### Post by Max Luebbe on 2007-08-17
or surround the file name with double quotes ex: "some file with spaces.txt"

---

### Post by wormser on 2007-08-17
> **Max Luebbe said:**
> or surround the file name with double quotes ex: "some file with spaces.txt"

Damn, I forgot that one.  But it reminded me of another technique.  When typing out a command use the **tab key** to auto complete the file name or command.

---

