---
title: "Gui sees drives, terminal does not"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-11-03
Using Gutsy live cd, the gui sees both of my hard drives, but I cannot see them from the terminal (or maybe I don't know how ...)

Gary

---

### Post by kellemes on 2007-11-03
type fdisk -l (with root privileges) to see all your partitions..

---

### Post by Gary Nored on 2007-11-03
I didn't phrase my question well, I suppose. I *can* see the drives via fdisk, but I *cannot* see the files or directories via ls. partimage can't see them either. I'm confused.

Gary

---

### Post by dcstar on 2007-11-03
> **Gary Nored said:**
> I didn't phrase my question well, I suppose. I *can* see the drives via fdisk, but I *cannot* see the files or directories via ls. partimage can't see them either. I'm confused.

Gary

You have to mount things to see files, look in /media.

Partimage does not work with files or directories, it works with disk partitions.

---

