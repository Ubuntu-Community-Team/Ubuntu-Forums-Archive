---
title: "ln -s"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-08-11
To change the target of a symbolic link, I usually remove the symlink and create a new one (with the same name) that points to a new target. Can we directly change the target of a symlink?

---

### Post by jordilin on 2006-08-11
Yes, type

```
ln -snf newtarget currentlinkname
```

---

### Post by mumebuhi on 2006-08-11
Thank you, jordilin.

It seems that I was having difficulty to understand the ln manpage.

-n, --no-dereference
treat destination that is a symlink to a directory as if it were a normal file

What is a "destination"? I thought destination = target, in this case.

---

