---
title: "banshee errors"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by insanitywetrust on 2007-01-31
hello
trying to install latest deb file for banshee

this is the error message :: 

Error: Dependancy is not satisfiable: libdbus-1-1

tried to install the libdbus-1-1

and get this error message :: 

loki4t4@alpha44:~$ sudo apt-get install libdbus-1-1
Reading package lists... Done
Building dependency tree... Done
Package libdbus-1-1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdbus-1-1 has no installation candidate
loki4t4@alpha44:~$

any suggestions on what to do?

am trying to get decent software to support the ipod shuffle and many Large mp3 files....

---

### Post by n8bounds on 2007-02-25
Do you have universe and multiverse repos enabled?

If that didn't help try a not so high version of banshee...  dbus is an important part of Ubuntu and trying to forcefully upgrade it may break other things you don't wish broken

---

