---
title: "help with wget"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by etusha on 2008-03-14
hello all 
i have a ask 
can i do that wget rename the downlaod file 
for example 
wget site.com/file.zip rename it 000000001.zip

---

### Post by Dr Small on 2008-03-14
You can not use wget to change files / filenames on a remote site.

---

### Post by etusha on 2008-03-14
i know that 
but i need that in my sever

---

### Post by drubin on 2008-03-14
```
wget site.com/mylongzipname.zip 
mv mylongzipname.zip   00000001.zip
```

That downloads, and then renames it after?

---

### Post by arvevans on 2008-03-14
_Suggestion:_    Make a specific directory for storing the site you copy with wget.  After that directory, and any sub-directories, contain the info you want to compress, use gzip with the -r option to make your compressed copy.

Use the man command to see how each command works:

[INDENT]man wget

man gzip[/INDENT]

You could write a small shell script program to automate the process by calling wget with the WebURL and follow that with the gzip -r to compress things when the wget was done.

Hope that helps,

Arv
_._

---

