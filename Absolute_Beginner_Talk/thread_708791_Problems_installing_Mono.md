---
title: "Problems installing Mono"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by gkrules on 2008-02-26
Well I just installed Ubuntu a few days ago. i have my video card and wireless working. but im still having trouble installing programs. One particular program i've had trouble with is Mono...i install it...it gets to 100% and then a window comes up and says

Missing libraries:
----------------
libgailutil.so.17 libglitz.so.1
----------------

It appears your system may be unable
 to run graphical apps included
 in this installer.  Please fix
 unresolved symbols by installing
 the necessary packages for your
 system.


and i have no idea how to get that library...
can someone help?
thanks in advance
:guitar:

---

### Post by AndyCooll on 2008-02-26
Why are you installing it manually?

As far as I'm aware there is no need to manually install it, it will be installed as and when needed by apps as part of their dependencies.

:cool:

---

### Post by PeterJS on 2008-02-26
If you're looking to program in mono, the mono-devel meta package should cover everything you need to get up and running.

---

### Post by gkrules on 2008-02-26
> **AndyCooll said:**
> Why are you installing it manually?

As far as I'm aware there is no need to manually install it, it will be installed as and when needed by apps as part of their dependencies.

:cool:


i am installing it to run RatioMaster by NPRG...and you have to install it manually

---

### Post by PeterJS on 2008-02-26
> **gkrules said:**
> i am installing it to run RatioMaster by NPRG...and you have to install it manually

Why? Does RaitoMaster require a version newer than what's in the repositories?

---

### Post by gkrules on 2008-02-26
> **PeterJS said:**
> Why? Does RaitoMaster require a version newer than what's in the repositories?

no idea...
here's the site tho
[http://ratiomaster.nrpg.info/](http://ratiomaster.nrpg.info/)

---

### Post by PeterJS on 2008-02-26
Hmm, what'da know, it requires mono 1.2.5, and the version in the repositories is 1.2.4, so looks like you do need a manual install, I'm sorry.

The package for libglitz is libglitz1, and the package for libgailutil is libgailutil18, which can be installed with:
```

sudo apt-get install libglitz1 libgailutil18

```

---

### Post by gkrules on 2008-02-26
> **PeterJS said:**
> Hmm, what'da know, it requires mono 1.2.5, and the version in the repositories is 1.2.4, so looks like you do need a manual install, I'm sorry.

The package for libglitz is libglitz1, and the package for libgailutil is libgailutil18, which can be installed with:
```

sudo apt-get install libglitz1 libgailutil18

```

wow sweet thanks man

---

### Post by gkrules on 2008-02-27
i just got around to trying it[my internet stopped working for a while] 
whenever i do it i get this

gkrules@gkrules-laptop:~$ sudo apt-get install libglitz1 libgailutil18
[sudo] password for gkrules:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgailutil18

and it doesnt install

---

### Post by mc4man on 2008-02-27
the package is libgail18 - which replaced libgail17 (what the installer is looking for)
related thread - [http://ubuntuforums.org/showthread.php?t=673835&page=2](http://ubuntuforums.org/showthread.php?t=673835&page=2)
hardy will have mono 1.2.6

---

### Post by PeterJS on 2008-02-27
Yeah, mc4man is right about that name of the package, sorry about that.

---

