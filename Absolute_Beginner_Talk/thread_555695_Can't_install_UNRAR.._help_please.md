---
title: "Can't install UNRAR.. help please"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by _deneb_ on 2007-09-20
HI everybody,

I tried to install unrar-nonfree because the free version doens't unpack some of my rar archives.

this is what I get

```
deneb@deneb-laptop:~$ sudo apt-get install unrar-nonfree
Reading package lists... Done
Building dependency tree... Done
Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar-nonfree has no installation candidate
```

why? :( help please!!! I'm sure I have multiverse and universe repositories added!
_deneb_:confused::confused:

---

### Post by Perfect Storm on 2007-09-20
please post the output;

```
cat /etc/apt/sources.list
```

---

### Post by FuturePilot on 2007-09-20
This is all you need
```
sudo apt-get install unrar
```
:)

---

### Post by _deneb_ on 2007-09-20
I tried what you wrote FuturePilot but it doesn't work. Same error...

```
deb http://it.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://it.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://it.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by Perfect Storm on 2007-09-20
Multiverse isn't enable;

You can set up a source here;

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by _deneb_ on 2007-09-20
I saved this list as sources.list using the mv command.

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://it.archive.ubuntu.com/ubuntu dapper main restricted 
deb http://it.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

deb-src http://it.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://it.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://it.archive.ubuntu.com/ubuntu dapper universe multiverse 
deb http://it.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb-src http://it.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://seveas.theplayboymansion.net/seveas dapper-seveas all 

deb-src http://seveas.imbrandon.com dapper-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://it.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 

deb-src http://it.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Upstream Wine
# GPG key: 387EE263
deb http://wine.budgetdedicated.com/apt dapper main 

deb-src http://wine.budgetdedicated.com/apt dapper main

# Upstream Opera
# GPG key: 6A423791
deb http://deb.opera.com/opera etch non-free 

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com dapper-commercial main 

deb-src http://archive.canonical.com dapper-commercial main
```


but it doesnt work still! :(
thnks so far

---

### Post by FuturePilot on 2007-09-20
Try
```
cat /etc/apt/sources.list
```
If it matches the one you just saved, you need to update the apt database
```
sudo apt-get update
```

---

### Post by Perfect Storm on 2007-09-20
You forgot which editor to use;

sudo nano /etc/apt/sources.list

[ctrl]+[o] = save

[ctrl]+[x] = exit

then;
```
sudo aptitude update && sudo aptitude upgrade
```

Note you might get some complain about keys issue. It's not errors but warnings to remove the warnings please read the lines in the automated generated source list on how to do it.

---

### Post by _deneb_ on 2007-09-20
I DID IT!!!
Thanks to all of you :D 

_deneb_

---

### Post by 5735guy on 2007-12-30
sudo apt-get install unrar

worked great for me:):)

---

