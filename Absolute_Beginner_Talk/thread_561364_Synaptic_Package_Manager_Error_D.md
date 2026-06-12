---
title: "Synaptic Package Manager Error :D"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Yelsew on 2007-09-27
I am currently getting the below error and cannot seem to fix it. Granted i am an absolute idiot at linux as of now, (just got it tree days ago).

E: Type 'n' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by swisscow on 2007-09-27
You have an error in your sources list it seems.

type:

```
gksudo gedit /etc/apt/sources.list
```

go to line 44 and have a look for the 'n' which shouldn't be there

Or alternatively post the list to the forum for advice

---

### Post by Yelsew on 2007-09-27
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
n## Beryl repository
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

---

### Post by JBAlaska on 2007-09-27
Change this line;
n## Beryl repository
to this:
## Beryl repository
Save and exit then restart Synaptic

Edit: Also looks like you have the wrong beryl repos installed so also change:
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

To:
## deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
## deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

---

### Post by Yelsew on 2007-09-27
^^ Thanks! That fixed it right up. Learning a new OS is a pretty complicated thing to learn. lol I changed entirely because I hate windows with a passion. XD

---

