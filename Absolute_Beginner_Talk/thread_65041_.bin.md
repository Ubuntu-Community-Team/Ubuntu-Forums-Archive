---
title: ".bin"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by cadaver on 2005-09-12
What do I do with files that end in ".bin"? I downloaded a program for Linux, but I don't know how to install it.

---

### Post by dcraven on 2005-09-12
[QUOTE=cadaver]What do I do with files that end in ".bin"? I downloaded a program for Linux, but I don't know how to install it.[/QUOTE]
```

chmod 755 whatever.bin
./whatever.bin

```

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=cadaver]What do I do with files that end in ".bin"? I downloaded a program for Linux, but I don't know how to install it.[/QUOTE]
Typically, you run them.  E.g.
```

$ cd downloads
$ ls -l
-rwxr--r--   1 user user   1503 Sep 11 22:37 myfile.bin
$ ./myfile.bin

```

---

