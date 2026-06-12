---
title: "Need help Updating"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-04-20
when i try to update i get this message:

E: Type '-e' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


what should i do?

---

### Post by EarlGrey on 2007-04-20
Could you post here the file /etc/apt/sources.list?

```
gedit /etc/apt/sources.list
```

.. a quick way to do that.

---

### Post by Benifited on 2007-04-20
this is what i get:

-e deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://en.archive.ubuntu.com/ubuntu/](http://en.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted #Added by software-properties
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

---

### Post by Bachstelze on 2007-04-20
Delete the first line and try again.

---

### Post by Benifited on 2007-04-20
> **HymnToLife said:**
> Delete the first line and try again.

i cant save it!!!!!!

---

### Post by Bachstelze on 2007-04-20
That's because tou need to run gedit with root privileges :

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Benifited on 2007-04-20
> **HymnToLife said:**
> That's because tou need to run gedit with root privileges :

```
gksudo gedit /etc/apt/sources.list
```

well i dont get the error anymore but the updates dont appear

---

### Post by Bachstelze on 2007-04-20
What do you mean, they don't appear ?

---

### Post by Benifited on 2007-04-20
> **HymnToLife said:**
> What do you mean, they don't appear ?

nvm  =p

---

