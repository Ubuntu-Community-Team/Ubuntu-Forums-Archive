---
title: "wheel group"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by careca on 2006-08-03
I'm trying to install a programm that fails because

```
symlink: Group [wheel] doesn't exist. Aborting!
```

What is this group about? Which program creates it?
It is safe to create it manually?

---

### Post by ciscosurfer on 2006-08-03
[Wheel Group]("http://www.kernel-panic.org/wiki/GroupWheel")

---

### Post by careca on 2006-08-03
Thank you!

/bin/su exist but not /bin/sudo. I changed for /usr/bin/sudo

It is OK?



and "chown o-rwx /bin/su /usr/bin/sudo" says me "o-rwx user not valid"

but i think is not important for my porpouses...

---

### Post by ciscosurfer on 2006-08-03
Yes, /usr/bin/sudo is correct.

Change 'chown' to 'chmod'.

---

