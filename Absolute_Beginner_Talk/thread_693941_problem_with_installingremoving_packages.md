---
title: "problem with installing/removing packages"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by traxxxx on 2008-02-11
Hello!

I have this problem with installing and removing packages, all started after i installed automatix and tried to install stuff with it.

now i can not install and not remove anything.

The error i get is:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing deskbar-applet (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

Using Dapper

---

### Post by taurus on 2008-02-11
Are you sure you did add the right version?  Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by traxxxx on 2008-02-11
ok here is the sources list


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


#AUTOMATIX REPOS START

deb [http://kubuntu.org/packages/koffice-152](http://kubuntu.org/packages/koffice-152) dapper main

deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) dapper main

deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END

---

### Post by taurus on 2008-02-11
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of all these lines to comment them out.

```

deb http://kubuntu.org/packages/koffice-152 dapper main

deb http://kubuntu.org/packages/kde-355 dapper main

deb http://kubuntu.org/packages/amarok-143 dapper main

deb http://wine.lowvoice.nl/apt dapper main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://www.beerorkid.com/compiz/ dapper main

deb http://people.ubuntu.com/~seb128/deb ./

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse

```
Save the changes.  Then, see what happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by traxxxx on 2008-02-11
ok i did all that but sill i get the same errors when doing apt-get update and when doing apt-get upgrade i get only this error

---

### Post by jan quark on 2008-02-11
automatix is not recommend by me

it causes severe problems with the compatibility of the packages

so please do not use it anymore

---

### Post by traxxxx on 2008-02-11
OK so i dont use automatix in future, but does anyone have any more suggestions for resolving the current problem i have, or is the only way to reinstall?

---

### Post by spiderbatdad on 2008-02-11
you might try commenting out the dapper backports as well, and make sure you saved the file. Then you might try```
sudo dpkg --configure -a
```

---

### Post by zvacet on 2008-02-11
Uninstall Automatix and put # in front of Automatix line in your source list.After that 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by traxxxx on 2008-02-12
Hey

I found a solution.

in /var/lib/dpkg/status file there was a wrong package name on Depends line.
After correcting it everything works fine

Thanks to everyone who gave advice ;)

---

