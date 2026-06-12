---
title: "tar.gz into deb file"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by lex1 on 2008-02-23
how to convert a tar.gz file into a deb file?


lex1

---

### Post by Duck2006 on 2008-02-23
You may find what you need on this link.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mkzimms on 2008-02-23
using check install instead of install will create a .deb...


```
sudo apt-get install checkinstall
```

while you compile from the source, checkinstall

```
./configure
make
sudo checkinstall
```

---

### Post by SOULRiDER on 2008-02-23
You might wanna check this out:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

