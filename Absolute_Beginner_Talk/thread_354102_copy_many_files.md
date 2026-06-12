---
title: "copy many files"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by holsv1 on 2007-02-05
Hi, I am using Ubuntu 6.10 server, and I just need to now how to copy many files from one folder to another at the same time?

Thanks

---

### Post by PriceChild on 2007-02-05
```
man cp
```Man is your friend :)

```
cp <<files/folders>> <<location>>
```You'll want -R right after the cp if you are copying a folder of files :)

---

### Post by Shatrat on 2007-02-05
Well, it depends on the files, but if you are in a directory with a bunch of jpeg images and you want to copy them to another directory you could use.
cp *.jpeg /path/to/other/directory
* is a wildcard and will match any filename.

---

### Post by Brunellus on 2007-02-05
> **Shatrat said:**
> Well, it depends on the files, but if you are in a directory with a bunch of jpeg images and you want to copy them to another directory you could use.
cp *.jpeg /path/to/other/directory
* is a wildcard and will match any filename.
use "cp" if you just want to make a copy:
```


cp foo.jpg /bar/baz/foo.jpg

```

if you want to move whole directories, recursively it's

```

cp -r foo bar

```

if you want to *move, replace cp with mv.

if you wanted to do it by filename or type, use a wildcard.  note that * doesn't work quite the same in bash as it did in DOS (that's CMD. EXE or command.com).  To copy all the jpgs in a directory to anothe directory it's

```

cp *jpg /some/other/dir

```

---

