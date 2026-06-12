---
title: "Missing Deb"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-08-03
I am missing a package that allows me to open deb files from the terminal.

```
deb http://www.example.com
bash: deb: command not found
```
What package do I need to install?

---

### Post by splintercellguy on 2007-08-03
If you want to install debs, then sudo dpkg -i mypackage.db. If you want to view them, file-roller does it. If you want a GUI way to install it gdebi.

---

### Post by physx on 2007-08-03
Are you trying to install a .deb package?  If so, I think you're looking for dpkg, not deb.  Let me know if I'm misunderstanding your post, though...

---

