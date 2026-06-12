---
title: "incomplete updates"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-01-06
I have kino on my desktop but when I receive the usual notices about system updates & click to execute them, I always get a message stating 'not all packages could be updated' and it is always kino that can't be upgraded.  Any reason for this?  Is it likely that kino is in active development with real updates being provided?  Kino still works but I've been curious why I keep getting notices of updates to it that can't then be installed!
Thanks.

---

### Post by riven0 on 2007-01-07
Something not configured perhaps? Try running **sudo dpkg --configure -a** and see if it gets rid of the problem.

---

### Post by flyingsolo on 2007-01-07
Thanks but after doing as suggested I get the following:

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  kino
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

...and this is my usual problem.  I know the version of Kino in the repositories is 0.8.0 and yet the current version at Kino's site is 0.9.4,  Why does the system "keep back" that particular upgrade?

---

### Post by riven0 on 2007-01-07
Maybe someone more knowledgeable will come in... but in the meantime, have you tried **sudo apt-get dist-upgrade** ?

---

### Post by flyingsolo on 2007-01-07
Thanks, but yes I've done the upgrade also.  I may consider just downloading the current version from Kino directly to bypass the upgrade via synaptic.  I'd just like to know the background as to why this happens

---

### Post by geezerone on 2007-01-10
I had the same problem which I bypassed by using "sudo apt-get remove kino" which uninstalled kino and kinoplus. Haven't tried installing it as no need for it but at least the message has gone. ;)

---

