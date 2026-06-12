---
title: "ubuntu 7.04 howto mount CD drive ?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by matiz on 2007-05-10
Hi:
I have upgrade to ubuntu 7.05 from 6.10, but can't mount the CD drive both manually or automaticly,
is this a bug ? or I have to do some more work ? :confused:

My CD drive is IDE.

---

### Post by [S|G] on 2007-05-10
You can try to manually mount it using this:
```
sudo mount /dev/scd0 /media/cdrom0
```
If it works at least you can use your CD, but Ubuntu should definitely mount it automatically for you.

---

