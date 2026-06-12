---
title: "FreeCiv Game"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by projectgonewrong on 2007-03-26
I try to install FreeCiv in the Advanced mode and it comes up with this error.

freeciv-client-gtk:
 Depends: libsdl-mixer1.2 (>=1.2.6) but it is not installable


How do I fix it? I tried searching libsdl-mixer but nothing came up. What do I do so I can play this game?

---

### Post by Bachstelze on 2007-03-26
Which Ubuntu are you running ?

---

### Post by projectgonewrong on 2007-03-26
5.10

---

### Post by Bachstelze on 2007-03-26
About time you upgrade... Anyway, libsdl-mixer1.2 definitely is in the Breezy repos. Could you please paste your source.list ?

---

### Post by projectgonewrong on 2007-03-26
I have no clue what that means...Im a noob. How do I get a source.list?

---

### Post by Bachstelze on 2007-03-26
First, have you tried to do that in a terminal ?

```
sudo apt-get update
sudo apt-get install freeciv
```

---

### Post by projectgonewrong on 2007-03-26
Okay I did that and after the second terminal entry it said this.

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freeciv: Depends: freeciv-client
E: Broken packages

---

### Post by Bachstelze on 2007-03-26
Hmm, try with *freeciv-client-gtk* then.

---

### Post by projectgonewrong on 2007-03-26
This is what it says now.

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freeciv-client-gtk: Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
E: Broken packages

---

### Post by Bachstelze on 2007-03-26
and what happens when you try to install libsdl-mixer1.2 ?

---

### Post by projectgonewrong on 2007-03-26
wesley@ubuntu:~$ sudo apt-get install libsdl-mixer1.2
Reading package lists... Done
Building dependency tree... Done
Package libsdl-mixer1.2 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsdl-mixer1.2 has no installation candidate

---

### Post by Bachstelze on 2007-03-26
All right, now we'll need your sources.list :

```
cat /etc/apt/sources.list
```

---

### Post by projectgonewrong on 2007-03-26
wesley@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by Bachstelze on 2007-03-26
OK, I fixed it for you, do :

```
cd
wget http://paste.ubuntu-nl.org/12196/plain/ -O sources.list
sudo cp sources.list /etc/apt
sudo apt-get update
sudo apt-get install freeciv-client-gtk
```

---

### Post by thefoolisme on 2007-03-26
I think it just doesn't like the old version of Ubuntu you're using.  I would upgrade it to 6.10, but that's just my $.02.  :KS

---

