---
title: "Still working to get sound!"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by oldnumber11 on 2006-05-24
My sound card is not recognized. It is a Riptide driver (from linuxant, linux drivers for Conexant chipsets). I downloaded the *TAR* package. I have it extracted, but when I run 'make install', nothing happens. Does ubuntu support RPM package manager? Any Ideas?](*,)

---

### Post by divague on 2006-06-18
To convert from rpm to deb, you could install alien with synatic and run this on the terminal:

sudo alien <name-of-the-file>.rpm

i will create a deb file and to install it:

sudo dpkg -i <name-of-the-deb-file>.deb

hope this helps.

---

