---
title: "installing files without internet connection"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by daloi on 2006-03-11
hello, im new at ubuntu & linux in general. how do i install files in my computer? my pc does not have an internet connection so i cannot just use the apt-get command. 

if i can download all the files for xmms, for example, and then copy it into my hard disk, how do i go about installing it?

---

### Post by Klaidas on 2006-03-11
You can install DEB packages with ```
dpkg -i file.deb
```
You can compile programs yourself ```
./configure
make
make install
```

However, I'm not sure if it takes care of dependencies. I'm a fan of apt-get :)

---

### Post by daloi on 2006-03-13
thanks for your help. really appreciate it.

---

### Post by meborc on 2006-03-13
btw, to get the same packages as using apt-get, go to **[http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)**

AND don't forget that you need ALL the dependencies, otherwise the program will not install... all the dependencies are also listed in the link above

---

