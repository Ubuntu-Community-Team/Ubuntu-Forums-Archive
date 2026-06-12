---
title: "Missing Something?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-07
darren@ubuntu:~/Desktop$ sudo dpkg -i cedega_5.0.1_i386.deb
Password:
Selecting previously deselected package cedega.
(Reading database ... 58827 files and directories currently installed.)
Unpacking cedega (from cedega_5.0.1_i386.deb) ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega

Im missing something i guess. Does anyone know where i can get xlibs? Or how i can get it?

Thanks

---

### Post by Rinzwind on 2005-12-07
xlibs is among my normal install-files
so it would be
> sudo apt-get install xlibs
for you.


BUT it'd inside 'oldlibs' AND says this:> 
name xlibs
summary X Window System client library transitional package

description
This package smooths upgrades from Ubuntu 5.04 ('Hoary') to Ubuntu 5.10 ('Breezy') by ensuring the smooth removal of all XKB configuration files that were formerly in the 'xlibs' package. If you are running Breezy already, you may safely remove this package.


So that's a bit odd :)

---

### Post by Rackerz on 2005-12-07
Thanks. Cedega is now installed :D.

---

