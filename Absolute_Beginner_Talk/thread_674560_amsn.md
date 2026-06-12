---
title: "amsn"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by aja on 2008-01-21
Hello


Does any one have any ideal what I am doing wrong ?? I ve loaded amsn 0.97 form add / remove as well as from synapic package manger. Both cases it show as being loaded OK, But when I start amsn. It does not start ??? All I see is a wheel go around for while then nothing.

---

### Post by PeterJS on 2008-01-21
Does it generate an error message if you try to launch amsn from a terminal? Generally running things from the terminal produces more descriptive error messages.

---

### Post by spiderbatdad on 2008-01-21
no idea, but i did use mercury messenger for a while. It works with msn and has video support if you go through the configuration instructions.

---

### Post by aja on 2008-01-21
me@me-desktop:~$ amsn
/usr/bin/amsn: line 3: exec: wish: not found


this what i get when i run in terminal.

---

### Post by PeterJS on 2008-01-21
> **aja said:**
> me@me-desktop:~$ amsn
/usr/bin/amsn: line 3: exec: wish: not found


this what i get when i run in terminal.

```

peter@Osirus:~$ apt-file search `which wish`
tk8.3: usr/bin/wish8.3
tk8.4: usr/bin/wish8.4
tkx8.3: usr/bin/wishx8.3
wordnet: usr/bin/wishwn
peter@Osirus:~$ 

```

Looks like wish is in the tk package with is a part of the tcl scripting language. Try installing tk8.4.

Edit:
How did you install aMSN? the deb requires tk8.4.

---

### Post by aja on 2008-01-21
Peter

I Reloaded that file and I get this message now " Loading TKCXimage failed. this modual is needed to run amsn. Please compile amsn firstInstructions are in the install file "

I am able to run it terminal  mode. So I am part way there. any Ideal what that message means ??

---

### Post by PeterJS on 2008-01-21
Well I don't know enough tcl to translate that error message in to a file name to derive a package name from. Have you tried uninstalling and re-installing?

---

### Post by aja on 2008-01-21
HI peter

Yes I tried that a few times

---

### Post by PeterJS on 2008-01-21
Got me. I assume you're installing from the repositories, so all the dependacies should be taken care of.

---

### Post by aja on 2008-01-21
I am using synaptic package manger to load.

---

