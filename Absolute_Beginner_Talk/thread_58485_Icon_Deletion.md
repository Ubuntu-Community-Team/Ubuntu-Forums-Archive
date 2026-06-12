---
title: "Icon Deletion"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by Rick069 on 2005-08-20
Suddenly I got all these icons on my desktop with little pad lock images on them and I can't delete them just like I can't delete the ones in the trash can. How can I get rid of these things?

And a simple way to create shortcuts?

---

### Post by heimo on 2005-08-20
On terminal, type:
```
sudo chown youruser:youruser ~/Desktop/*
chmod u+w ~/Desktop/*

```
click on desktop and hit F5. No longer padlocks.

Oh, and "shorcuts" are links. Right click on file, choose Make Link, move the link (created in same directory) where you want it.


EDIT: Darn.

---

