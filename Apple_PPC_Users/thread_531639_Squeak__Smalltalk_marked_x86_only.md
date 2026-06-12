---
title: "Squeak / Smalltalk marked x86 only ?"
date: 2007-08-21
forum: Apple PPC Users
---

### Post by rectagonal on 2007-08-21
squeak, squeak-images and squeak-sources are all available for PPC users, but they rely on squeak-vm which has no package for PPC users...

The source for squeak-vm compiles on PPC and squeak.org provides linux/PPC binaries... just curious why it's not in the repositories.

Tried using prevu to compile it on my system, and it seems to compile fine, just gets rejected afterwards as it claims my architecture isn't supported...

I can use the binaries provided by squeak.org just fine, just wish I could use my regular package manager..... Also I notice x86 users have a nice little menu before they open up Squeak that lets them pick which image to work on.... which I suspect is an Ubuntu improvement, id like to have access to.

---

### Post by stmiller on 2007-08-22
Looks like no one on the ubuntu package team has bothered to make anything but an x86 deb. You can file a bug report to request a powerpc deb. But yeah you'll have to just fetch it from the squeak homepage, at least for now.

---

