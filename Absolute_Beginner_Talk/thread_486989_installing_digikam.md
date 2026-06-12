---
title: "installing digikam"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by rlutker on 2007-06-28
I have ubuntu 6.06 on my computer.  I would like to install Digikam 0.9.1, but the neweest version in the package manager is digikam 0.8.2.
How do I install Digikam o.9.1 from source?  What dependencies will I have to install first?  Where do I find these dependencies?

---

### Post by chandler on 2007-06-28
[http://www.mpe.mpg.de/~ach/kubuntu/edgy/Pkgs.php](http://www.mpe.mpg.de/~ach/kubuntu/edgy/Pkgs.php)

They have a .deb on there which should auto-resolve dependencies.

---

### Post by rlutker on 2007-06-28
I tried installing the deb and I got a dependency error

---

### Post by stmiller on 2007-06-28
Point your /etc/apt/sources.list to feisty and install from the ubuntu feisty repos.

---

### Post by rlutker on 2007-06-29
How would I do that?

---

### Post by Subetealabici on 2008-01-30
Hello 
I have the same problem trying to install digikam 9 at 6.06, I have install digikam 0.8 but the option to make a movie with pictures is not working.

To edit the repositories list you can 

gksu gedit /etc/apt/sources.list

---

### Post by airbornemist6 on 2008-01-30
as sube just said edit your sources.list. Replace all instances of dapper with feisty.

---

### Post by bodhi.zazen on 2008-01-30
> **rlutker said:**
> How would I do that?

> **airbornemist6 said:**
> as sube just said edit your sources.list. Replace all instances of dapper with feisty.

Oh, that is not such a good idea (mixing repos) unless you know what you are doing. Basically you would need to update fapper -> Feisty, but you should not skip version in between, so

6.06 -> 6.10 -> 7.04 -> 7.10

I advise you try from source, check the home page for a list of dependencies, and post errors you get here.

---

