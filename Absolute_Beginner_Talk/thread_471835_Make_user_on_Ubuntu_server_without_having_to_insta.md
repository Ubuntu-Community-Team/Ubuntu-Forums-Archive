---
title: "Make user on Ubuntu server without having to install GUI"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Jimmyfj on 2007-06-12
Hi

I'm a newbob and having searched almost all corners of the online manuals I still can't figure out how to add new user to my server and how to make/change user passwords - Help PLZ, anyone

---

### Post by Seisen on 2007-06-12
If I remember correctly it is this

```
adduser
``` or variation of that.

---

### Post by p_quarles on 2007-06-12
Assigning a password depends on the system your using. For Samba, it's smbpasswd [user].

Both commands need some variables and arguments, though, so be sure to man them first.

---

