---
title: "Wine Problems"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Lex-Man on 2007-03-04
I have been trying to install wine on a AMD64 based machine following the Wiki page

[https://help.ubuntu.com/community/WineForAMD64#head-5a11b1bb5c50bdd2ef4abb4143b1e570468f6f8c](https://help.ubuntu.com/community/WineForAMD64#head-5a11b1bb5c50bdd2ef4abb4143b1e570468f6f8c)

But when I try and force install wine I get the following warning

ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

I have checked and the file exists does anyone know what file I have to link to?

---

### Post by Lex-Man on 2007-03-04
I found a post telling me to run the command

sudo apt-get install ia32-libs

I have run it and it hasn't stopped my problem.

Any ideas?

---

