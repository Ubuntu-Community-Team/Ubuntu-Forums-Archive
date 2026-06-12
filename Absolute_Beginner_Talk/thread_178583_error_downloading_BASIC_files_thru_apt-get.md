---
title: "error downloading BASIC files thru apt-get"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by KiranF on 2006-05-17
so i am trying to install wine, and i need libgtk1.2 so i try to run:

sudo apt-get install libgtk1.2

i get the following error:

Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk1.2 has no installation candidate

i ran apt-get update too, but that didn't seem to do anything

What is going on??

---

### Post by aysiu on 2006-05-17
Sounds as if you have conflicting and/or non-existent repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by KiranF on 2006-05-18
thanks! that worked!

---

