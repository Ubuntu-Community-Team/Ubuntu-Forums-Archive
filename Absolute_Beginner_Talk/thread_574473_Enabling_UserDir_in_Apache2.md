---
title: "Enabling UserDir in Apache2"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by photoRat on 2007-10-12
Hey,

After some research I found a way to enable UserDir in Apache2

All I had to do was copy 

userdir.conf
userdir.load

from /etc/apache2/mods-available/
 to /etc/apache2/mods-enabled/

plus of course you have to have a public_html folder in each users home folder

then point your browser at [http://localhost/~user](http://localhost/~user)

I am sure this is somewhere in the fm, but I must have missed it.:guitar:

go figure..

photoRat

---

### Post by kidders on 2007-10-14
> **photoRat said:**
> All I had to do was copy 

userdir.conf
userdir.load

from /etc/apache2/mods-available/
 to /etc/apache2/mods-enabled/Normally, people symlink those files, rather than copying them, just as you would with the sites-available & sites-enabled directories.

---

