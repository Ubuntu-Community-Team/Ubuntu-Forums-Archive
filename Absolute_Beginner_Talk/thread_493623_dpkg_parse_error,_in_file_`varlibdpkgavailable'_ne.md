---
title: "dpkg: parse error, in file `/var/lib/dpkg/available' near line 18299"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-05
I can't install anything, even using the terminal, it comes up with this error.
```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 18299:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

The attachment below is of that entire file. Please help!

---

### Post by Maxtorm on 2007-07-06
A quick scan of some Google results would seem to indicate that you can delete the **available** file and it will recreate itself, though I would suggest renaming rather than deleting:
```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.old
```
and then do a sudo apt-get update.

---

### Post by az on 2007-07-06
I would suggest the normal way:

sudo dpkg --clear-avail

---

