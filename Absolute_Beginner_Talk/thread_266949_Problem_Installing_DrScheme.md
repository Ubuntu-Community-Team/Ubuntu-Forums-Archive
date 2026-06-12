---
title: "Problem Installing DrScheme"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by curtisf14 on 2006-09-28
Hi everyone,

I've searched the forums and google for any help on this problem, but no luck.  I am trying to install DrScheme via Synaptic (I try to install the drscheme package), but when I mark it for installation, it gives me the following error:

```
drscheme:
Depends: mzscheme but it is not going to be installed
```

So I try to install mzscheme, and it basically takes me on a wild goose chase of packages that it can't install until I get to some packages (like libreadline5-dev, which depends on a specific version of libreadline5) for which the installed version is incorrect.  However, if I go to "force version..." and pick the required version of libreadline5 that I need, it tells me that Synaptic needs to remove a LOT of packages, including pretty much all of gnome and many of my installed programs (and I clearly don't want to uninstall everything else just to install DrScheme).  libreadline5 is just one of the few packages it does this with.

Any ideas on what may be going on here?  Am I doing something wrong, or do I possibly have too many/too few repositories selected?  Any help would be very appreciated.  Thanks!

---

### Post by Sef on 2006-09-28
> ny ideas on what may be going on here? Am I doing something wrong, or do I possibly have too many/too few repositories selected? Any help would be very appreciated. Thanks!

What repositories have you enabled?

---

### Post by digby on 2006-09-28
I think I remember (from a while ago) someone filing a bug about that particular package.  As an alternative, you can download DrScheme (that they compiled specifically for Dapper) from [here.]("http://download.plt-scheme.org/drscheme/plt-352-bin-i386-linux-ubuntu-dapper-sh.html")

To install, just run the file (sh whatever_the_file_name_is.sh)

---

### Post by curtisf14 on 2006-09-28
> **Sef said:**
> What repositories have you enabled?


I have the following in my sources.list file:

```

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main
 restricted


deb http://archive.ubuntu.com/ubuntu breezy main restricted
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
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe
 multiverse
# deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted univ
erse multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://security.ubuntu.com/ubuntu breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse


```


Thanks!  And digby, I'll try installing it from the place you posted.  However, it seems like I've had this problem with a few other packages too (like installing krb5 or something), but I can't remember which packages it was.

---

### Post by curtisf14 on 2006-10-01
Of course!  The problem is that I'm using Dapper, but when I used EasyUbuntu to get flash and dvd stuff working, it changed all my repositories to Breezy!

A good warning to users: [COLOR="Red"]when using EasyUbuntu, remember to change your sources list back to Dapper.[/COLOR]

---

