---
title: "[SOLVED] Quickly installing dependencies"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Riverbanks on 2008-02-03
Hi, I was wondering if there was a way to install several dependencies for a package I'm compiling at once, for example, I'm trying to install Avant Window Navigator 0.2.1, and I keep having to install all the packages it depends on, one by one, which is a real hassle.

I'm just looking for a way to find out what the dependencies for a package are, and install them all at once.

---

### Post by jan quark on 2008-02-03
try to run this

```
sudo apt-get install build-essentials
```

might help it installs all the well essentials for compiling

---

### Post by Riverbanks on 2008-02-03
Nope, tried that, the package could not be found.

---

### Post by jan quark on 2008-02-03
sry

```
sudo apt-get install build-essential
```

typo without the s

---

### Post by Riverbanks on 2008-02-03
It seems I already have that installed...
But I don't have any problems with compiling in general, I'm trying to find out a way to install all the dependencies for a specific package in one shot.

---

### Post by jaytek13 on 2008-02-03
There is not really a way to accomplish that when compiling from source, other than using synaptic and doing searches for all the dependencies and marking them for installation.

---

### Post by jan quark on 2008-02-03
I guess jaytek13 is correct

compiling is fun...

---

### Post by Riverbanks on 2008-02-03
Hmmmmm....

Well, is there a way to just get a list of the dependencies for a package?  Since it stops compiling when it encounters a package it doesn't have, I'd have to install them one by one as they come up anyway.

---

### Post by jan quark on 2008-02-03
hey try this 
it is much more easier

[http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu](http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu)

---

### Post by Riverbanks on 2008-02-03
That worked, thanks.

---

### Post by jseiser on 2008-02-03
just to answer your question.  When you install something from source their is normally, a readme file, that lists all the depencies you need, and the command to install the program.  so get the dependcies in that list then, sudo apt-get app1 app2 app3 app4 app5 etc.

---

### Post by jan quark on 2008-02-03
please mark this thread as solved using the thread tools
thank you

---

