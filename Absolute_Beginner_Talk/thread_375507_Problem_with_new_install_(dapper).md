---
title: "Problem with new install (dapper)"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by gholen on 2007-03-03
```
http://se.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.bz2: Subprocess bzip2 returned error (2)
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.bz2: Subprocess bzip2 returned error (2)
```


This has been like that for two daus, I have tried it all.
I'v tried to reinstall, I've tried to recover, as I said, all.

Please help me!

---

### Post by Bachstelze on 2007-03-03
Try this :

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-get update
sudo mv /etc/apt/sources.list.old /etc/apt/sources.list
sudo apt-get update
```

Same error ?

---

### Post by gholen on 2007-03-03
```
89% [37 Packages bzip2 0] [44 Packages 1824440/2458kB 74%] [45 Packages 8187/95
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fel http://archive.ubuntu.com dapper/universe Packages
  Underprocessen bzip2 returnerade en felkod (2)
Läs:46 http://se.archive.ubuntu.com dapper/universe Sources [975kB]
88% [44 Packages bzip2 2658304] [46 Sources 95984/975kB 9%]          239kB/s 3s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Wrong http://se.archive.ubuntu.com dapper/universe Packages
```


thats the awnser to that one.

I don't know why... Please, help me, I am desperate. Thanks in advance!


EDIT EDIT!
It says that it wint install updates from ubuntu because of faulty md5 checksums.
Anyone knows Why?
Thacks in advance!
END EDIT

---

