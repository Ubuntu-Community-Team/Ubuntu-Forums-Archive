---
title: "Mythtv on powermac g5"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by rothgar on 2006-09-15
I have been searching all over and I have not found any way to get mythtv to install/build using ubuntu and a g5 powermac.  I would prefer to use the latest 0.20 myth that was released but I have been having problems building it from scratch.  Some people have told me to go over to gentoo but I would rather use a OS that I have on other computers.
Does anyone know of a repository with any version of myth for the PPC?
How about drivers for the video cards? (this one has a nvidia fx 5200 but there are no nvidia drivers for the PPC arch)
are there any walk throughs to build mythtv from svn or source on a PPC?
Any help would be greatly appriciated.
Thank you.

---

### Post by stmiller on 2006-09-15
Finding a ppc linux tv card may be the problem. USB tv cards will probably work best, if they have philips chipsets, or other ones that are Linux friendly.

Let me try building the new release from source and see what happens. Seems fairly straight forward in the documentation.

[http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4)

---

### Post by stmiller on 2006-09-15
Okay it builds fine from source for me, on PPC. Make sure you have these files installed:

libqt4 files
libttf
lame-dev
mysql-server
libqt3 files

libxxf86vm-dev

And any others it complains of needing while compiling. Good luck!

---

