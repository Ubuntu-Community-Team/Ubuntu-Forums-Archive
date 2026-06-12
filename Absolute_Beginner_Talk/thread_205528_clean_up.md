---
title: "clean up"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Stromham on 2006-06-28
is there any program i can use to clean up my ubuntu system? i want to clean it up and "defrag it" how would i accomplish this?

---

### Post by xtacocorex on 2006-06-28
I downloaded a program that did (cleanup) this in Breezy, I just can't think of it's name.

EDIT:
Found it: kleansweep in the unverse repos.
[http://packages.ubuntu.com/dapper/kde/kleansweep](http://packages.ubuntu.com/dapper/kde/kleansweep)

---

### Post by aysiu on 2006-06-28
I'm not sure that defragmentation is really necessary.

---

### Post by az on 2006-06-28
[QUOTE=Stromham]is there any program i can use to clean up my ubuntu system? i want to clean it up and "defrag it" how would i accomplish this?[/QUOTE]
Deborphan will remove packages that have no dependencies.  Other that that, the filesystem does not fragment unless you use up all of your disk space.

---

### Post by aysiu on 2006-06-28
[QUOTE=azz]Deborphan will remove packages that have no dependencies.  Other that that, the filesystem does not fragment unless you use up all of your disk space.[/QUOTE]
*gtkorphan* is the graphical frontend for *deborphan*.

If you want dependencies removed along with a package (provided no other package depends on them), install packages with *aptitude* instead of *apt-get*.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

