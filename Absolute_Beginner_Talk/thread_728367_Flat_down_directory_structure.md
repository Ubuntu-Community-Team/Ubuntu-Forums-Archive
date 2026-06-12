---
title: "Flat down directory structure"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Peach.Zeta on 2008-03-18
Hi All, 

I would appreciate if somebody could help me finding how to flatten down a directory structure while  preserving all file thereby contained. In other words, something like:

Directory A has 10 files
Directory A/B has 5 files

After processing, the end result should be:

Directory A has 15 files
Directory A/B has 0 files
(the five files in A/B are moved to A/ and removed)

It is actually not important whether files in directory A/B are deleted or not, I could delete the entire B directory afterwards.

Thanks in advance,
Carlo

---

### Post by nick_h on 2008-03-18
You can use the *mv* command to move files.
```
mv A/B/* A
```
will move all the files in directory A/B into A.

---

### Post by Peach.Zeta on 2008-03-19
Thanks Nick,

maybe my question was not detailed enough.

Imagine some thing more complicated:

A/ has 10 files
A/B has 5 files
A/B/C has 87 files
A/D/ has 100 files
A/C/D has 120 files

I need to move files in sub-directories of A into A. Folder names might be repeating underneath two or more given path. 

Thanks,
Carlo

---

### Post by nick_h on 2008-03-19
You can use *find* with the *-exec* option as follows:
```
find . -type f -exec mv '{}' . \;
```
This will move all files below the current directory into the current directory.
You can replace the "." (current directory) with another.
You should also run the find command on its own first to see what files will be moved as follows:
```
find . -type f -print
```

---

