---
title: "Package installation problem"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by hoppy on 2007-07-17
Hi all,

I'm trying to get php4, php4-mysql, libapache2-mod-php4 working on my desktop but when I try to install using apt I get the following:

[B]john@helion:~$ sudo apt-get install php4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php4 has no installation candidate
[/B]
My sources.list is:

[B]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty restricted main universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END[/B]

As far as I can see I don't have any problems install other packages.

Thank you.

Hoppy

---

### Post by felicity on 2007-07-17
You can do a 
```

apt-cache search php4

```
or
```

apt-cache search php

```
to see some related packages in the repositories.

It doesn't look like there is any php4 there, perhaps php5 will work for you?

---

### Post by useResa on 2007-07-17
Why are you going for php4? Searching my (Feisty) repositories 
Why not install php5, php5-mysql and libapache2-mod-php5?
My guess is you are setting up a LAMP server and personally I only use php5 for this now.

One more comment: Am I misreading something in your sources.list but do you still have some references to edgy repositories. The lines I mean are
> deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by hoppy on 2007-07-17
Hi useResa,

> **useResa said:**
> Why are you going for php4? Searching my (Feisty) repositories 
Why not install php5, php5-mysql and libapache2-mod-php5?
My guess is you are setting up a LAMP server and personally I only use php5 for this now.


I'm doing web development and the sites I'm currently working use php4.

Thanks for pointing out the edgy sources. I'm not sure how they got there :oops: but I've commented them out now.


Hoppy

---

### Post by useResa on 2007-07-17
As can be read in [this Ubuntu question]("https://answers.launchpad.net/ubuntu/+question/5312") php4 is completely removed from the Feisty repositories.
> There shouldn't be any php4 packages left in feisty. All php4 related packages were removed. Php applications which depended on php4 were changed to depend on php5. If there is still a package depending on php4 than that's a bug and should be reported if not already happened.
Therefore I think your only option is either to go back to Edgy or use php5.


Don't worry about the Edgy repositories left, you can also uncomment them and alter edgy in feisty ;)

---

