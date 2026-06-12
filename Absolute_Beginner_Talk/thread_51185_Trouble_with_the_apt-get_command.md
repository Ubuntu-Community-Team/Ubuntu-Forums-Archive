---
title: "Trouble with the apt-get command"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by bursto22 on 2005-07-22
When i try the 

sudo apt-get install nvu

command (after i have apdated) i get this error

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvu: Depends: libgnomevfs2-0 (>= 2.9.90) but 2.8.2-0ubuntu1 is to be installed
E: Broken packages
``` 

what do i need to do?
This error comes up for all apt-get install attempts

---

### Post by Xian on 2005-07-22
Have you added the backport repos to your [sources.list](http://ubuntuguide.org/#extrarepositories)?

---

### Post by bursto22 on 2005-07-22
Yes i have done that
here is my sources.list file

```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

about a month ago iwas able to install scribus with the apt-get install command so i dont know why this has stopped working

Thanks Ba

---

### Post by poofyhairguy on 2005-07-22
Didi you update?

> sudo apt-get update

---

### Post by bursto22 on 2005-07-23
Yes-the updater seems to work fine

---

