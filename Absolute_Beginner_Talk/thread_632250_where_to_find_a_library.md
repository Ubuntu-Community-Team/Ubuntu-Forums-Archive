---
title: "where to find a library"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by bijave on 2007-12-05
Hi !

I need a library which name is : libstdc++.so.5
Where can I find it ans install it ?

---

### Post by OffAxis on 2007-12-05
check your 
/usr/lib
folder.
If you've got gcc v3.3 installed it should be there.

Going from here
[http://www.joewein.de/sw/swnotes002.htm]("http://www.joewein.de/sw/swnotes002.htm")

you may need to put a link in the local folder.

```
ln -s /usr/lib/libstdc++.so.5 /usr/local/lib/libstdc++.so.5
ln -s /usr/lib/libgcc_s.so.1 /usr/local/lib/libgcc_s.so.1
```

(opposite commands from the hyperlink)

---

### Post by Hospadar on 2007-12-05
if you arn't sure if you have it installed, you can install gcc and the build tools and it will get installed
```
sudo apt-get install build-essential
```or install it from synaptic.

Also, you can just search for "libstdc++5" in synaptic, find the package, check if it's installed, if not, install it, then you can right-click the package, go to properties, and have a gander at the "installed files" and find the file you're looking for

Also note that having this without having "build-essential" isn't going to be super useful, so I would suggest installing build-essential instead of just this library

---

### Post by bijave on 2007-12-05
Thanks!
I solved my problem with your help.

---

