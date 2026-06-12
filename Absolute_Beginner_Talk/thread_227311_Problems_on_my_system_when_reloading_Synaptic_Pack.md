---
title: "Problems on my system when reloading Synaptic Package Manager"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-01
Hi everyone,

When I reload Synaptic Package Manager, I get the following errors...

> W: Duplicate sources.list entry [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)


Does anyone know how to sort this out please?

---

### Post by ajgreeny on 2006-08-01
It looks as though you have duplicated lines in your /etc/apt/sources.list.

Open the that file to check using gedit or any text editor and look for lines containing:-
deb [http://uk.archive.ubuntu.com]("http://uk.archive.ubuntu.com/") dapper-updates/multiverse Packages
and
deb [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) dapper-updates/universe Packages.

There may be two identical lines in the file which are causing the error message.  If so close the copy of the file you have open and reopen the file as root (gksudo gedit /etc/apt/sources.list) and comment the duplicate lines by putting a # at the start of the line.  Save the file and try synaptic again.  Hopefully, all will now be OK.

---

