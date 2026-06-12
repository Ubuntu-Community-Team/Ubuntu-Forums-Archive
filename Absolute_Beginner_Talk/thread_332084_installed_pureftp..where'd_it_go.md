---
title: "installed pureftp..where'd it go?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by iQuizzle on 2007-01-05
This is probably an easy question to answer. I just installed pure ftp. I did the usual ./configure and make install. Then I exit root and go to usr/local/sbin and it's not there. How can I figure out where the program installed to?

---

### Post by taurus on 2007-01-05
It's probably in /usr/local/bin!

```
ls -la /usr/local/bin
```
Otherwise, run

```
locate pureftp
```

---

### Post by iQuizzle on 2007-01-05
nothing happened when I typed locate pureftp.  I checked usr/local/bin and this was all that was there:

```
drwxr-xr-x  2 root root 4096 2007-01-05 14:13 .
drwxr-xr-x  9 root root 4096 2005-01-06 23:27 ..
-rwxr-xr-x  1 root root 5880 2007-01-05 14:13 example_read
-rwxr-xr-x  1 root root 5568 2007-01-05 14:13 example_write

```


those are files that it installed with pureftp, but I still cant find the program itself.

---

### Post by taurus on 2007-01-05
```
sudo find / -name pureftp* -print
```

---

### Post by iQuizzle on 2007-01-05
nada :/

---

### Post by taurus on 2007-01-05
Did you run "**make install**" or "**sudo make install**" after ./configure & make?

---

### Post by iQuizzle on 2007-01-05
i just ran "make install" as root user

---

### Post by taurus on 2007-01-05
Don't you need to run make after ./configure and before make install?

```

./configure
make 
make install

```

---

