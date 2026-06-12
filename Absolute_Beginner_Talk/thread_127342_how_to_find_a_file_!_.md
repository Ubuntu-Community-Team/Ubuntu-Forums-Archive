---
title: "how to find a file_!_"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-02-08
I cant seem to be able to find out the equivelent of dos/s

DIR filename* /S

command. Is there another command or something

---

### Post by BenTyreman on 2006-02-08
Either run
```
sudo updatedb
locate filename

```

Or
```
find / -iname "*filename*"
```

---

### Post by David Corrales on 2006-02-08
The command **which** is also useful because it only searches for executables like **ls, cd, man**...

---

### Post by taurus on 2006-02-08
Or

sudo find / -name <filename> -print

---

