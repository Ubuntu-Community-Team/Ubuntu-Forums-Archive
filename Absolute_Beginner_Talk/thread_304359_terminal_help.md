---
title: "terminal help"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-11-21
ok, im trying to navigate to my steam directory.
unfortunately, after i get into drive_c, i cant get into program files. i think its because of the space, here is what i put in:
```

tony@tony-computer:~/.wine/drive_c$ cd program files
bash: cd: program: No such file or directory

```

is there any way to get into this file through terminal?

---

### Post by taurus on 2006-11-21
```
cd "program files"
-or-
cd program\ files
```

---

### Post by 23meg on 2006-11-21
Put it in quotes, or use a backslash for the space

```
cd "Program Files"
```or ```
cd Program\ Files
```

---

### Post by Cardmaster91 on 2006-11-21
thanx

---

