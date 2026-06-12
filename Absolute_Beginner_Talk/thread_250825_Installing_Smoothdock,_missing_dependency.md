---
title: "Installing Smoothdock, missing dependency"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Guillaumeb on 2006-09-04
Can someone guide me here? When trying to run the .deb file it says :
dependency not satisfiable: kdelibs4

I am really lost here how can I install this required dependency?

I have naively tried apt-get install kdelibs4
 this is what i get:

guillaumeb@guillaumeb-laptop:~$ sudo -s
root@guillaumeb-laptop:~# apt-get install kdelibs4
Reading package lists... Done
Building dependency tree... Done
Package kdelibs4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2a
E: Package kdelibs4 has no installation candidate

So I try with the package mentionned:

root@guillaumeb-laptop:~# apt-get install kdelibs4c2a
Reading package lists... Done
Building dependency tree... Done
kdelibs4c2a is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@guillaumeb-laptop:~#

then I retry opening the deb file with GDebi Package installer but the same error occurs concerning kdelibs4

For information I am using Ubuntu and I have installed KDE on it.

thank you very much

---

### Post by Iarwain ben-adar on 2006-09-04
Hi,
i'm just guessing, but try installing kdelibs4c2a-dev ...

It could be just that :D


Iarwain

---

### Post by Guillaumeb on 2006-09-04
Hi thanks for you answers; unfortunately it did not work:

guillaumeb@guillaumeb-laptop:~$ sudo -su
sudo: please use single character options
Password:
root@guillaumeb-laptop:~# apt-get install kdelibs4c2a-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kdelibs4c2a-dev
root@guillaumeb-laptop:~#


any other suggestions?

thank you

---

### Post by Iarwain ben-adar on 2006-09-04
well,

can you try to fire up the graphical apt-get? (Synaptic/Adept)

Search for kdelibs4, and see if you could install via that (unlikely), but maybe you see the -dev package for it ;)


Iarwain

---

### Post by Guillaumeb on 2006-09-04
well I have found some information but honestly it does not mean much too me !!
[http://packages.debian.org/stable/libs/kdelibs4](http://packages.debian.org/stable/libs/kdelibs4)

---

### Post by Iarwain ben-adar on 2006-09-04
Hi,
doesn't mean much to me either :)

Did synaptic bring you any results?


Iarwain

---

### Post by Guillaumeb on 2006-09-04
no I could not find it with or without unsupported options...

---

### Post by Iarwain ben-adar on 2006-09-05
Then i don't know what it could be...

Sorry


Iarwain

---

