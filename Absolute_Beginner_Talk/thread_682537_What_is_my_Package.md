---
title: "What is my Package?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-30
Hello!
I wanted to report some bugs(for edubuntu hardly), but launchpad wanted me to write my package name.```
hooman@hooman-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu hardy (development branch)"
hooman@hooman-laptop:~$ dpkg -l PKGNAME | cat
No packages found matching PKGNAME.
```
This was what I got. What should I type for the package?
Thank you.

---

### Post by kpkeerthi on 2008-01-30
Package names will usually be like kernel-headers, totem, mplayer, nautilus, build-essential etc. A package is... well... a package of  files including executables that are part of an application. 

There is no package in Ubuntu by name PKGNAME. Replace PKGNAME with whatever application name you are trying to file the bug under.

---

### Post by Hoom@n on 2008-01-30
I wanna report one for weather report (which you can add to pannel) and I couldnt find the package. Please tell me what is it?
And one for the graphics which I'm sure there is no package for this!
Thank you,

---

### Post by mcduck on 2008-01-30
The PKGNAME in this command ("dpkg -l PKGNAME | cat") should be replaced with the name of the package/program you are having problems with.

So, for example, if it's a Firefox bug the command would be  "dpkg -l firefox | cat".

---

### Post by Hoom@n on 2008-01-30
Thanks, but I wanted to know the weather report's package name.

---

