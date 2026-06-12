---
title: "error in apt-get"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Makaai on 2007-07-16
I got this
```
dpkg: syntax error: invalid uid in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
and I can't install or upgrade anything.:confused:
any help?

---

### Post by twiceasworn on 2007-07-16
Has this been happening since you installed Ubuntu or did it just start recently?  If it just started ocurring, have you changed anything?

---

### Post by Makaai on 2007-07-16
I have ubuntu from one month but it starts two days ago to gave this error...I think the only change I made that I didn't undestand so much what I've done it was when during installing a package it gaves me this
```
configure: error: QTDIR environment variable must be set
```
and then someone suggested me to run
```
export QTDIR=/usr/include/qt3
```
tha I really don't lnow what means...about other stuff,nothing special I think

---

### Post by splintercellguy on 2007-07-16
Have you tried running sudo apt-get -f install?

---

### Post by twiceasworn on 2007-07-16
Well the command you issued exported the path to your qtlibs.  Are you sure that is the actual path of where your QTlibs are?  If it isn't then I would bet that would not help anything.

---

### Post by Makaai on 2007-07-16
@splinter: yes, it doens't help

@twice:no,I'm not sure,but I'm also not sure this may be the cause of my trouble.It was a supposition

---

