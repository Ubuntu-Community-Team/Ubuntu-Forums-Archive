---
title: "Problems using Alien, missing file"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by gmx on 2006-08-18
Hello everyone,

I'm new to these forums, finished installing ubuntu yesterday, partitioned the harddrive w/o problems *whew* and now I'm trying to get the rest of my crap to work:

Printer: Lexmark Z605, OEM drivers are only provided for Red Hat (RPMs).
I found [this post]("http://www.ubuntuforums.org/archive/index.php/t-83456.html").
Ad per the all the instructions... installed libstdc++5 and alien as per README and INSTALL.
Ok so I managed to extract the 2 .rpm files and when I type in this (sudo -i):
alien -t --scripts z600cups-1.0-1.i386.rpm

and get this:
rpm2cpio: error while loading shared libraries: libdb.so.2: cannot open shared object file: No such file or directory
rpm2cpio: error while loading shared libraries: libdb.so.2: cannot open shared object file: No such file or directory
cpio: premature end of archive
z600cups-1.0.tgz generated

tgz file is created but there is nothing in it...
i tried reinstalling alien just to make sure, found alien-extra which claims to include all the needed files, and yes i check that i copied them to the right paths. "libdb.so.2" is indeed missing, it couldn't find it in any of alien's archives which leaves 3 options:
1. fix alien
2. find another converter
3. use printer from windows... (that would defeat the whole purpose)

anyway, any obvious places i should be looking?

---

### Post by croak77 on 2006-08-18
Install libdb1-compat if it isn't already. That provides libdb.so.2.

---

