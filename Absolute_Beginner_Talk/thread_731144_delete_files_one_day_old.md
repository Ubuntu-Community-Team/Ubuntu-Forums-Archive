---
title: "delete files one day old"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by etusha on 2008-03-21
i need to create cron job to delete files one day old in specific directory

---

### Post by spiderbatdad on 2008-03-21
Not sure if this is ideal, but short of writing a sed/awk program to do it, you can clear a file by being root and using the ">" (greater than sign) then path/to/file. I would assume you could make that small script, make it as root, and put it in the appropriate cron folder.

For example, as root create a text file called ClearUserLog.sh```
#!/bin/bash
> /var/log/user.log
```

save it in /etc/cron.daily and make it executable.

I have no idea how this will work, but I'm going to try it. lol.:)

---

### Post by lloyd_b on 2008-03-21
> **etusha said:**
> i need to create cron job to delete files one day old in specific directory

```
find {directory} -mtime 1 -delete
```

Will remove all files in {directory} that are between 24 and 48 hours old.  Is this what you were looking for?

Lloyd B.

---

### Post by asmoore82 on 2008-03-21
> **etusha said:**
> i need to create cron job to delete files one day old in specific directory

It is important to note here that UNIX filesystems do _NOT_ store the time a file was created.
So, the only attribute to look at for "one day old" is file **modification** time.
from the `find` **manpage**:
[QUOTE="man find"]-type c
              File is of type c:
              b      block (buffered) special
              c      character (unbuffered) special
              d      directory
              p      named pipe (FIFO)
              f      regular file
...
Numeric arguments can be specified as
       +n     for greater than n,
       -n     for less than n,
       n      for exactly n.
...
-mtime n
File’s data was last modified n*24 hours ago.  See the comments for -atime to
understand how rounding affects the interpretation of file modification times.[/QUOTE]

So, to list **regular files** in <location> with a **modification time** older than 1 day:
```
find <*location*> -type f -mtime +0
```
and to **permanently** delete those same files:
```
find <*location*> -type f -mtime +0 -exec unlink '{}' \;
```
But be careful!

---

### Post by asmoore82 on 2008-03-21
> **lloyd_b said:**
> ```
find {directory} -mtime 1 -delete
```

Will remove all files in {directory} that are between 24 and 48 hours old.  Is this what you were looking for?

Lloyd B.

Ahh Open Source at its best, you can combine our solutions and achieve this:
```
find <*location*> -type f -mtime +0 -delete
```

---

### Post by etusha on 2008-03-24
i have try 
> find /var/www/vhosts/mysite.com/httpdocs/tmp -mtime 1 -delete
but dont work

---

### Post by forrestcupp on 2008-03-24
You need sudo

---

