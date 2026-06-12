---
title: "Help to install mtpaint"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-09-09
Hi
I'm trying to install mtpaint on Ubuntu 6.06 Dapper.
I've downloaded and unzipped the tar.bz folder.
In the Readme file it says:-
For GTK+2
=========

./configure
make
su -c "make install"

For GTK+1
=========

./configure gtk1
make
su -c "make install"

I've changed to the relevant directory and
I've tried various combinations of these but with no luck. Are there different commands to use with Dapper?

---

### Post by powder on 2006-09-09
Did you install package "build-essential"?

---

### Post by ron999 on 2006-09-09
Hi powder

It was already installed, I've just checked in Symatic and it's there ok.

---

### Post by powder on 2006-09-10
The likely problem here is you are missing some dependencies that are required for the source to compile.  The output of the error should give you some hints.

---

### Post by ron999 on 2006-09-10
Hi
Is there someone else that can help me please?
Which commands are needed to install this program on Ubuntu 6.06?

---

