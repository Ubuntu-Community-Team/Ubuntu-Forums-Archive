---
title: "[Apt-get] Broken Packages Problem"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by DiamondX on 2006-07-03
On my laptop, I have a problem. When I was trying to get 3d drivers for my 950GM, I followed the dri.sourceforge.net debian tutorial (no ubuntu tut.). In the tutorial, it said to add a repository. The tutorial didnt work, and it downloaded new versions of some packages. Now I have 2 broken packages. The computer still works, and I want to fix it, without reinstalling. I sshed it (I dont like the touch pad thing). Here is what happened:
```
austin@Desktop:~$ ssh austin@192.168.0.100
austin@192.168.0.100's password:
Linux Laptop 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Jul  3 13:10:43 2006 from 192.168.0.106

austin@Laptop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
E: Unmet dependencies. Try using -f.

austin@Laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
austin@Laptop:~$
```

Any ideas?

---

### Post by byen on 2006-07-03
looks like a simple dependency issue. Whenever you get any dependency issues.. try the following to fix the errors:
```
sudo apt-get -f install
```
See if that helps... goodluck.

EDIT: I just noticed that you have done a sudo apt-get install -f which should have taken care of the dependencies. But looks like you have more dependenices that you might have to install manually as the current versions are being used by other programs. Just try googling if you can find those files and then install them. Sorry mate.. I wish i could have been of better help.

---

### Post by DiamondX on 2006-07-03
[QUOTE=DiamondX]```
...austin@Laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
austin@Laptop:~$
```[/QUOTE]
I did do sudo apt-get install -f. I guess it wasnt obvious. I better edit it a little bit...

---

### Post by byen on 2006-07-03
Gah! I did not realaize that you did that already! Sorry mate!

---

### Post by DiamondX on 2006-07-03
No problem. Does anyone else have any ideas? I basically want to revert my programs to the version in the official repos, which are previous versions than the ones I have installed.

---

### Post by richbarna on 2006-07-03
[QUOTE=DiamondX]No problem. Does anyone else have any ideas? I basically want to revert my programs to the version in the official repos, which are previous versions than the ones I have installed.[/QUOTE]

I think you made a typo, take a look at your post:-
> .austin@Laptop:~$ [COLOR="Red"]sudo apt-get install -f[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.

And the other by byen :-
> sudo apt-get -f install

---

### Post by richbarna on 2006-07-03
[QUOTE=DiamondX]No problem. Does anyone else have any ideas? I basically want to revert my programs to the version in the official repos, which are previous versions than the ones I have installed.[/QUOTE]

Ok, I think I understand, you need to edit your sources.list.
In the terminal type :-
> gksudo gedit /etc/apt/sources.list

Wait for gedit to open, and either delete the repo URL that you added or delete everything and copy and paste mine :-
> 
##Ultimate Dapper Sources List

##Standard Ubuntu Packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Automatix (PGP Key: 521A9C7C)

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

##Wine

##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

##Seveas Packages Not Included In Ubuntu

##deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras
##deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras

##Cipherfunk multimedia packages (PGP key: 33BAC1B3)

##deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
##deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

##Dapper PLF

##deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free



Then do :-
> sudo aptitude update && sudo aptitude upgrade

---

### Post by DiamondX on 2006-07-04
richbarna: I copied your sources.list, did sudo apt-get update, and it updated fine. Then, when I did sudo aptitude upgrade, it gave me the same error:
```
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed.
  libc6: Depends: tzdata which is a virtual package.
```

I really want to get it working today/early tomarrow, because I am going to a friends house with my laptop, and I want to install Xgl and show it to him. Maybe convert him to linux, he currently uses a pirated winxp.

Edit: I _think_ the problem is that debian repos updated my packages with ubuntu-incompatable versions. Does anyone know of a way to down-grade all programs whos version is higher than in the repositories?

---

