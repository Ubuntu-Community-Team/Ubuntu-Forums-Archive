---
title: "I need libstdc++2.10-glibc2.2 to install the nxclient"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by eliasavila on 2006-07-20
Hello,
I need to install the Nomachine NXclient but, I can't find the libstdc++2.10-glibc2.2

I try this:

sudo apt-get install libstdc++2.10-glibc2.2

and this is the result:

Reading package lists... Done
Building dependency tree... Done
Package libstdc++2.10-glibc2.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++2.10-glibc2.2 has no installation candidate

Please help me out to fix this

---

### Post by Perfect Storm on 2006-07-20
Have you enable universe in your sourcelist?

---

### Post by eliasavila on 2006-07-20
How can I do That?


Thank in Advance


Elias Avila

---

### Post by Perfect Storm on 2006-07-20
```
sudo nano /etc/apt/sources.list
```

You'll find line that looks similiar to this:

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

Uncomment all you have a # infront.

so it looks like:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted



If you want all kind of extra stuff check at: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by PingunZ on 2006-07-20
just go to applications -> accessories -> Terminal
there type ```
gksudo gedit /etc/apt/sources.list
```
Uncomment everything ( remove the # 's ;) )
save and close the file
in that terminal now type ```
sudo apt-get update 
```
now you can install your software

---

### Post by eliasavila on 2006-07-20
It doesn't work I still have the same problem.
Maybe this is part of another Lib.:-k

---

### Post by eliasavila on 2006-07-20
FIXED...:)   I did what PinguinZ said and that it!!! Work

sudo apt-get update

Thank you very much

---

