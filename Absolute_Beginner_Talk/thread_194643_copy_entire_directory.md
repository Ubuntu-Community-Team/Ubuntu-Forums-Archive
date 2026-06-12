---
title: "copy entire directory"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-06-11
How would i go about copying the entire contents of a directory into another?

---

### Post by gerbman on 2006-06-11
[QUOTE=notquitehere188]How would i go about copying the entire contents of a directory into another?[/QUOTE]Open a terminal, and type```
cp -R <directory 1>/* <directory 2>
```where <directory 1> is the name of the directory whose contents you want to copy, and <directory 2> is the directory into which you want to copy the files. The "-R" option says to copy things recursively from the source directory, meaning it will copy sub-directories of <directory 1> as well. Make sure to include the "/*" after the directory path if you want to copy just the contents of <directory 1>.

---

### Post by elemental666 on 2006-06-12
alternatively you can use mv as follows:

```

mv <source dir> <destination dir>

```

the destination dir can have the same or a different name.  the benifit to doing it this way is it will remove the source dir from your system.  So if your wanting to make a copy (and retain the source dir) use cp, if you want to move the dir (and not retain the source dir) use mv.

---

### Post by aysiu on 2006-06-12
Or just open your favorite file manager (Konqueror or Nautilus), right-click the folder, select **Copy**, and go to the desired destination and right-click there and select **Paste**--same as Windows.

---

### Post by elemental666 on 2006-06-12
for clarity:

cp = copy/paste
mv = cut/paste

---

