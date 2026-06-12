---
title: "etswitch install problem"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by gunhippy on 2007-10-07
Total newbie here.

I'm trying to install Etswitch, a program that minimises a few games. It's a .tar.gz file.

I read a bunch of info on how to set it up, and it stops at

"checking for main in -lXpm... no"

Then tells me it needs it.  Sounds simple enough, but i can't find any info on what this is.

Can anybody explain what this is/ how to install it?

This happens during "./configure"

Thanks

-andy

---

### Post by gunhippy on 2007-10-07
I fixed it, and figured i'd post to leave a solution for anybody searching for the same problem in the future.

Essentially, i added

deb [http://security.debian.org/debian-security](http://security.debian.org/debian-security) sarge/updates main 

to my synaptic manager, then found and installed

libxpm-dev

which contained whatever libraries (or whatever it was) the program needed.

Simple solution really, but i guess it's how you learn =]

-andy

---

