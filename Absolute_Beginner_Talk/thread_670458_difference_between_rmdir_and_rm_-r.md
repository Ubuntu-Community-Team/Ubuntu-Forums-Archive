---
title: "difference between rmdir and rm -r"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-17
I don-t understand the difference between rmdir and rm -r.

In the tutorial it says

**rmdir: The rmdir command will delete an empty directory. To delete a directory and all of its contents recursively, use rm -r instead.**

BUT rmdir does not delete the folder...

---

### Post by steeleyuk on 2008-01-17
rmdir deletes a directory unless its empty.

rm -r recursively deletes a directory and anything in it.

---

### Post by stchman on 2008-01-17
> **ben22 said:**
> I don-t understand the difference between rmdir and rm -r.

In the tutorial it says

**rmdir: The rmdir command will delete an empty directory. To delete a directory and all of its contents recursively, use rm -r instead.**

BUT rmdir does not delete the folder...

rmdir stands for remove directory

rm -r stands for remove recursively.

rm is a more powerful and potentially destructive command and is analogous to DOS deltree.

---

