---
title: "where does it go?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-09-14
If I delete something from ```
/root/.trash
```, where does it go?
I deleted an item of 400 MB approx, and I have to delete it permanently to increase free space; what should I do?
It is not in .Trash-root, nor in /home/saurav/.trash

---

### Post by por100pre1 on 2007-09-14
It should be gone, for good.

---

### Post by sauravbhaumik on 2007-09-14
> **por100pre1 said:**
> It should be gone, for good.

It should have gone, but it did not :(
Actually, the size (free space) of my ubuntu partition was 4.7 GB; so if it were gone (for good), the size should have been 5.1 GB or so. But it has NOT changed a bit! Then?

---

### Post by por100pre1 on 2007-09-14
Check with this command:

```
df -h
```

You can also check with Baobab:

```
sudo aptitude install gnome-utils
```

Try locating the file:

```
locate *name-of-file*
```

---

