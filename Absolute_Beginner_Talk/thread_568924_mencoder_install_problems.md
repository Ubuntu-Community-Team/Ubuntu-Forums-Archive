---
title: "mencoder install problems"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by greg_suomi on 2007-10-06
Hi,

I have problems to install mencoder, when i try to install it i get:

gregoire@gregoire-desktop:~$ sudo apt-get install mplayer mencoder
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

I am running  Xubuntu 6.06
gregoire@gregoire-desktop:~$ uname -a
Linux gregoire-desktop 2.6.15-29-k7 #1 SMP PREEMPT Mon Sep 24 17:31:22 UTC 2007 i686 GNU/Linux

What can be the solution ?

Thanks for any hints or advice or howto !

gregoire.

---

### Post by greg_suomi on 2007-10-07
UP

Please, I would really love to know what this means:

sudo apt-get install mencoder
Password:
Reading package lists... Done
Building dependency tree... Done
Package mencoder is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
**E: Package mencoder has no installation candidate**

Because i know that mencoder shoud install OK!

thanks,

gregoire.

---

### Post by tdrusk on 2007-10-07
run 
```
sudo aptitude update
```

---

### Post by greg_suomi on 2007-10-07
> **fuzzyhair said:**
> run 
```
sudo aptitude update
```

Pretty much the same, i use synatpic or ap-get to fetch software, so i reload before using.
I just dont get what is wrong with this mencoder.

---

### Post by tdrusk on 2007-10-07
make sure your multiverse repository is open.

---

### Post by greg_suomi on 2007-10-07
> **fuzzyhair said:**
> make sure your multiverse repository is open.
What would be the best way to check that?

---

### Post by tdrusk on 2007-10-07
> **greg_suomi said:**
> What would be the best way to check that?

system>administration>synaptic

settings>repositories

---

### Post by greg_suomi on 2007-10-07
> **fuzzyhair said:**
> system>administration>synaptic

settings>repositories

Yes, I did it check the boxes at first install.

---

