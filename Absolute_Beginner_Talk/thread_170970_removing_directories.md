---
title: "removing directories"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-05-05
Is there anyway to remove directories without completely emptying them first. I use windowmaker so I need to know how to do it from the command line. Thank you.

---

### Post by aysiu on 2006-05-05
```
rm -rf *directoryname*
```

---

### Post by TheFourElements on 2006-05-05
cool. thanks. I was trying to use the rmdir command.

---

### Post by zerhacke on 2006-05-05
rm -rf /path/to/directory

Asyiu got to it before me.

---

### Post by umberleigh on 2006-05-15
Thanks.

Is there any reason rmdir --ignore-fail-on-non-empty /path/to/dir is failing? (that's what I tried first)

---

