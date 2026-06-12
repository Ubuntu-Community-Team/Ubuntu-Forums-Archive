---
title: "Won't let me save read-only file, even using su"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by seaworthy4life on 2007-06-06
Tried this:

$gksudo gedit /etc/apt/sources.list

and this:

$sudo vim /etc/apt/sources.list

to add new repository:

 ## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

No matter what, it will not let me save the end result.  In vim, I have tried :wx , :wq , and :wq! , all to no avail.  What I am I doing wrong?

---

### Post by Lord Illidan on 2007-06-06
> **seaworthy4life said:**
> Tried this:

$gksudo gedit /etc/apt/sources.list

and this:

$sudo vim /etc/apt/sources.list

to add new repository:

 ## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

No matter what, it will not let me save the end result.  In vim, I have tried :wx , :wq , and :wq! , all to no avail.  What I am I doing wrong?

Are you using apt-get/synaptic/add-remove/updater at the same time?

---

### Post by alienexplorers on 2007-06-06
apt-get, aptitude,and synaptic plus all other programs using sources must be off in order to edit it.  You are correct in using
> gksudo gedit /etc/apt/sources.lst

---

### Post by seaworthy4life on 2007-06-06
This probably takes a command.  How do I do that?  I don't see any other way to.

---

