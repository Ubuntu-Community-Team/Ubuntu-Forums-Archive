---
title: "Installing ushare"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-07-06
I'm trying to install this program:

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

but when using the proper i386 deb package, I get this error:

[IMG]http://img399.imageshack.us/img399/2793/debwg5.png[/IMG]

It also comes up when I try to install it manually.

What exactly does it mean, and how might I go about installing ushare?

---

### Post by lbelloq on 2007-07-06
It means you lack some libraries required to install the package. Try opening a terminal (Applications->Accesories->Terminal) and writing "sudo apt-get install [library_name]". If that works, try installing the package again.
The library name is that text after the red "Dependency is not satisfiable:".

---

### Post by phoenix23 on 2007-07-06
It said I already have the latest version of libc6

Tried to download ushare in terminal and get this error

stephen@stephen-desktop:~$ sudo apt-get install ushare
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ushare: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
          Depends: libupnp2 but it is not installable
E: Broken packages
stephen@stephen-desktop:~$

---

### Post by jdevora on 2007-07-09
Looks like they updated the package and it depends of a newer version of lthe ibc6 library than the one that comes with Ubuntu.

I have version 0.9.10-ubuntu1  of ushare and I can't upgrade due that same conflict.

The only solution that I can come up right now is compiling it from source.


Cheers
 JD

---

### Post by jdevora on 2007-07-11
Another option is download manually the previous version of ushare from [http://downloads.sourceforge.net/ushare/ushare_0.9.10-0ubuntu1_i386.deb](http://downloads.sourceforge.net/ushare/ushare_0.9.10-0ubuntu1_i386.deb)

And install the package manually.

Cheers
 JD

---

