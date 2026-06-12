---
title: "How do I install Tovid on Ubuntu?"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by okey on 2005-07-11
Can't quite get the hang of it.

---

### Post by tikal26 on 2005-07-11
What problems are you having. What have you tried so far. I would first make sure that i have all the dependencies install. Use synaptic.

---

### Post by okey on 2005-07-11
[QUOTE=tikal26]What problems are you having. What have you tried so far. I would first make sure that i have all the dependencies install. Use synaptic.[/QUOTE]

I just generally have no idea how to install it. If you can give me a step by step, I would very much appreciate it.

---

### Post by sapo on 2005-07-11
I dont think tovid have a deb package.. btw... to install it from cvs use this:

```

mkdir tovid_cvs
cd tovid_cvs
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tovid login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tovid co -P tovid
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tovid co -P gui

```

---

### Post by andy.parry on 2005-08-20
The files below downloaded OK for me and I think I have tovid installed OK, but I cannot get the GUI to install. The documents contained in the package say use the ./configure command, but the configure file seems to be missing. 

Or am I doing something wrong?

Andy
 ](*,) 


[QUOTE=sapo]I dont think tovid have a deb package.. btw... to install it from cvs use this:

```

mkdir tovid_cvs
cd tovid_cvs
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tovid login
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tovid co -P tovid
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/tovid co -P gui

```[/QUOTE]

---

### Post by andy.parry on 2005-08-22
Managed to find a copy of the GUI on FRESHMEAT, intact, with the config file installed. Easy when someone puts a package together correctly !  \\:D/ 

Andy

---

### Post by sapo on 2005-08-22
[QUOTE=andy.parry]Managed to find a copy of the GUI on FRESHMEAT, intact, with the config file installed. Easy when someone puts a package together correctly !  \\:D/ 

Andy[/QUOTE]

yep.. now they have a tar.gz of the last version 0.20 at:

[http://tovid.sourceforge.net](http://tovid.sourceforge.net)

by the time i ve posted that cvs stuff they didnt release the version as tar.gz

---

