---
title: "How to install a tar.gz package or a rpm package?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by abadoki on 2006-03-31
I am an absolute beginner with linux, and I am trying to install a tar.gz package that I download to my desktop, I have extracted to the desktop as well.  How to I install this package?  I can also download the package as a rpm.  Can anyone help?

---

### Post by Mustard on 2006-03-31
[http://www.ubuntuforums.org/showthread.php?t=153118](http://www.ubuntuforums.org/showthread.php?t=153118)

What is the package?

---

### Post by abadoki on 2006-03-31
The package is Avast4 for Linux, an anti-virus program.  I have installed alien, but it will not convert the rpm package, it says I must change to root or use fakeroot???

I 'm really lost.

---

### Post by abadoki on 2006-03-31
Here is the actual message.

jeff@ubuntu:~$ alien avast4workstation-1.0.4-1.i586.rpm
Must run as root to convert to deb format (or you may use fakeroot).
jeff@ubuntu:~$

---

### Post by Mustard on 2006-03-31
[QUOTE=abadoki]Here is the actual message.

jeff@ubuntu:~$ alien avast4workstation-1.0.4-1.i586.rpm
Must run as root to convert to deb format (or you may use fakeroot).
jeff@ubuntu:~$[/QUOTE]

Ah ok..I didn't realise that HOW TO had an error in it. :)

It should have instructed you to use 'sudo alien', that is to run alien as a superuser with the sudo command.  Try this...

```
sudo alien avast4workstation-1.0.4-1.i586.rpm
```

I've contacted the author of the HOW TO and informed him of the error in the HOW TO.  It's a work in progress atm. ;)

---

