---
title: "cant get to upgrade"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2007-04-27
when ever i try to upgrade my 6.10 t0 7.10 i keep getting this error

Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz) Unable to fetch file, server said 'Can't open /debian-marillat/dists/etch/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
  what must i do.

---

### Post by bapoumba on 2007-04-27
You need to comment out these debian repositories (add a **#** at the beginning of the line).
Open the sources.list file in a terminal (>Accessories > Terminal):```

sudo nano -B /etc/apt/sources.list
```
Add the #
Save the file with CTRL-O (same name, hit <enter>) and exit nano with CTRL-X.

Reload the repository list:
```
sudo aptitude update
```

In any case, you can paste your sources.list file:
```
cat /etc/apt/sources.list
```

---

