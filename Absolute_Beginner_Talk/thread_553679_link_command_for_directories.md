---
title: "link command for directories?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by angelochen960 on 2007-09-18
Hi,

I know link or ln can create a symlink to a file, is there a similar command for directories? example, Thanks, A.C.

---

### Post by Jussi Kukkonen on 2007-09-18
ln works but I believe you need to use a symbolic link (use the "-s" argument):

```
ln -s target dir
```

---

### Post by kerry_s on 2007-09-18
same thing as the files

ln -s /path/to/folder /path/you/want/a/link

example:

ln -s /media ~/media

you can name your link what ever you want to

ln -s /media ~/computer

---

