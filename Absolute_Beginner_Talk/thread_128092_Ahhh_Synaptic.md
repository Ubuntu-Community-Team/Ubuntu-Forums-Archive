---
title: "Ahhh Synaptic"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by mztriz on 2006-02-10
```
banshee:
  Depends: libgconf2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libglade2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libglib2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libgnome2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libgtk2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libipod-cil (<0.5.6+svn20050924+revertedto0.5.5) but 0.5.12-0filefind.net-breezy0 is to be installed


```
what's going with this? I tried to install Mono and it's givning me the same types of things it's saying I need things installed that I already have installed.

---

### Post by JNowka on 2006-02-10
I installed it under Kubuntu yesterday with no problems, but I download all the file manually from [http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by Murgle on 2006-02-10
do you have any special entried in your sources.list?  it looks to me like it's trying to install a version that is too advanced or slightly different and not backwards compatable of some files that something else needs.

---

### Post by mztriz on 2006-02-10
[QUOTE=Murgle]do you have any special entried in your sources.list?  it looks to me like it's trying to install a version that is too advanced or slightly different and not backwards compatable of some files that something else needs.[/QUOTE]
I already had that version installed I uninstalled it and I was going to reinstall it when that error ocurred. I already edited my sources.list I was using that version of banshee because of last.fm and it was working fine but today it was doing some weird things so I tried to reinstall it and .... yeah.

---

### Post by Murgle on 2006-02-10
well it still looks to me like your comp wants to install newer versions or different ones that aren't with compatable with another program your trying to install

---

### Post by mztriz on 2006-02-11
[QUOTE=Murgle]well it still looks to me like your comp wants to install newer versions or different ones that aren't with compatable with another program your trying to install[/QUOTE]
how do I install them because it says I already have the latest versions if I look up those things.

---

### Post by aysiu on 2006-02-11
Something's wrong with your sources.list. Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by Murgle on 2006-02-11
well I'm not sure then if youtr computer thinks it's up to date...  Did you try installing it with other packages or just by it's self?  I f you were trying to install many packages it might have conflicting dependancies than some other package

---

### Post by mztriz on 2006-02-11
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde35 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

---

### Post by mztriz on 2006-02-11
ohhh i figured it out, for some reason deb [http://apt.filefind.net/](http://apt.filefind.net/) breezy main contrib non-free wasn't in my sources anymore :-?

---

