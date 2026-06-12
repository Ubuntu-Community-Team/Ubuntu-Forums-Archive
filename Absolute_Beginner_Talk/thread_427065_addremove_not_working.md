---
title: "add/remove not working"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by maitresse on 2007-04-29
I keep getting this message:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

When i open a terminal and use  '/etc/apt/sources.list'. I get ~ Permission Denied.

Can anyone help me!?

---

### Post by Sef on 2007-04-29
Did you do this ```
gksudo gedit /etc/apt/sources.list
```?

---

### Post by maitresse on 2007-04-29
tried that, and i got

(gedit:6632): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then I got

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
## created by arniemaxremoved


Does that help?

---

### Post by Sef on 2007-05-02
> deb [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free

I would comment out those two lines.  PLF is not longer in operation.  To comment out put a # before each line.

Thus those two lines would look like this:

> 
#deb [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free
#deb-src [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free

Also I would update to a newer version of Ubuntu, since Breezy is no longer supported.

---

