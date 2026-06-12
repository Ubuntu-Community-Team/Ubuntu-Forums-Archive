---
title: "Where to put icons?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Duppy on 2007-01-19
Downloaded a icon package.

Its a blue version of human.

Where do I put it? I have a folder inside is 12x12, 32x32 and so on..

---

### Post by taurus on 2007-01-19
Most of the icons usually go in /usr/share/pixmaps.

---

### Post by Duppy on 2007-01-19
i dont have permission.

---

### Post by taurus on 2007-01-19
Use the sudo command from a terminal or run 

```
gksudo nautilus
```

---

### Post by IYY on 2007-01-19
Individual icons usually go to 

```
/usr/share/pixmaps/
```

However, entire icon themes go to
```

/usr/share/icons/

```

For either one of the above options, you need to make sure you are a superuser when you move the files there, and also set the permissions for all users to read.

An easier options is to put the icons in
```

~/.icons/
```

This will have the same effect, but the icons will only be usable by you (and not the other users on the computer).

---

### Post by Duppy on 2007-01-19
thanks mate thats wt i needed

---

