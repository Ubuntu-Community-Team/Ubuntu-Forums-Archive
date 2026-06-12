---
title: "Update Problem"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-01-31
Hello,
Whenever I run synaptic or update manager I get this error:
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

And I am NOT using Kubuntu.
Thanks,
Linuxnovice.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=linuxnovice]Hello,
Whenever I run synaptic or update manager I get this error:
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

And I am NOT using Kubuntu.
Thanks,
Linuxnovice.[/QUOTE]

Try editing your sources list. Here is a how to on how to do it.

[How To Enable Extra Repositories]("http://www.psychocats.net/linux/sources.php")

Edit: after you do this open the terminal and type ```
sudo apt-get update
```  and see if that does the trick.

---

### Post by morphodone on 2006-01-31
please show the contents of your /etc/apt/source.list

```
cat /etc/apt/sources.list
```

---

### Post by linuxnovice on 2006-01-31
Hello,
sources.lst:
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

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## created by arniemaxremoved
Linuxnovice.

---

### Post by morphodone on 2006-01-31
You can just disable the kubuntu repository.

```
##deb http://kubuntu.org/packages/kde35 breezy main
```

Then just update again.

```
sudo apt-get update
```

---

### Post by linuxnovice on 2006-01-31
Thanks!
Linuxnovice.

---

