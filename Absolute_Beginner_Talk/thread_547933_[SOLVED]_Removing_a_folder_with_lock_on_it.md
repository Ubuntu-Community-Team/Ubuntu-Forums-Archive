---
title: "[SOLVED] Removing a folder with lock on it"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Johnny3 on 2007-09-10
I was trying to install RealPlayer and got a folder on my Desktop with a lock on it. How do I remove it? I have tried  in terminal  sudo rm/home/johnny/Desktop/RealPlayer and sudo rmdir/home/johnny/Desktop/RealPlayer. Never did get RealPlayer installed. Any ideas how to remove the folder.
Thanks Johnny3
Gainesville Fl

---

### Post by Beggar on 2007-09-10
What about
```

sudo rm -rf /home/johnny/Desktop/RealPlayer

```

---

### Post by Johnny3 on 2007-09-10
That did it Thanks. What does the -rf mean?
Thanks Johnny3
Gainesville Fl

---

### Post by Beggar on 2007-09-10
straight from the man pages:
```
man rm
```

       -r, -R, --recursive
              remove directories and their contents recursively

       -f, --force
              ignore nonexistent files, never prompt

---

### Post by Daveth on 2007-09-10
type 

```
man rm
```

for the answer- it gives all the switches for that command.

---

