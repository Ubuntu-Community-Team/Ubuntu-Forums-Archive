---
title: "Synaptic repostries error"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2006-11-13
All right ... i was reading from ubuntu unleashed and i went here
[http://img145.imageshack.us/img145/664/screenshotan3.png](http://img145.imageshack.us/img145/664/screenshotan3.png)

clicked on edit then clicked on universe and multiverse and then i edited the source entry by adding multiverse and universe and then i clicked on ok
and then clicked on reload. I got the following errors

 [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)
<amit_> [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)
<amit_> [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

here are my sources.list

 [http://pastebin.com/823268](http://pastebin.com/823268)

Anyhelp would be appreciated 

TK

Amit

---

### Post by taurus on 2006-11-13
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by dead_man_walking on 2006-11-13
not working ... still get the errors

---

