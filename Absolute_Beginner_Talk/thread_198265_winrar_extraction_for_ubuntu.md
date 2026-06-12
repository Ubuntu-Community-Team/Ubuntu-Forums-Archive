---
title: "winrar extraction for ubuntu?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-16
Hi,

What is the best winrar type application for ubuntu. To extract rar 3.0 files. Everything I have looked at so far doesn't work.

Thanks.

---

### Post by x64Jimbo on 2006-06-16
Have you tried xarchiver? It's in the repo's.

---

### Post by tronica on 2006-06-16
have you tried installing unrar

> sudo apt-get install unrar

then do

> man unrar

for the man pages

---

### Post by u.b.u.n.t.u on 2006-06-16
Thanks. I did just then and it failed. It also wouldn't close.

I need extract rar version 3.0 files.

---

### Post by x64Jimbo on 2006-06-16
Maybe wine will run winrar? it's probably a pretty simple program.

---

### Post by u.b.u.n.t.u on 2006-06-16
Thanks tronica, but:

sudo apt-get install unrar
```
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
```

man unrar
```
No manual entry for unrar
```

---

### Post by nalmeth on 2006-06-16
```
nalmeth@dapper-drake:/usr/games$ apt-cache search unrar
unrar-free - Unarchiver for .rar files
unrar - Unarchiver for .rar files (non-free version)
``` 
try the unrar-free, if it doesn't work, then uncomment the restricted portion on your sources.list to get the non-free version

I think this should allow you to unrar with any of your apps like file-roller or ark

---

### Post by u.b.u.n.t.u on 2006-06-17
I have unrar free but I don't know where it is. Also,
"Unrar can extract files from .rar archives. Can't handle archives in the
RAR 3.0 format, only the non-free "unrar" package can do that"

I installed "unrar" and it worked.

Thank you.

:D 

PS It would be good if linux could support RAR 3.0 format.

---

### Post by Corvair on 2006-06-25
Thanks for the great tip.

I had the same problem. 
After installing unrar I was able to extract the files.

;)

---

### Post by FredB on 2006-06-25
[QUOTE=Corvair]Thanks for the great tip.

I had the same problem. 
After installing unrar I was able to extract the files.

;)[/QUOTE]

Unrar is in multiverse repository. And it was one of the first multiverse package I added ;)

---

