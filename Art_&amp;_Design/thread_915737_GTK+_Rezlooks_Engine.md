---
title: "GTK+ Rezlooks Engine"
date: 2008-09-10
forum: Art &amp; Design
---

### Post by Faolan84 on 2008-09-10
This is a 64-bit package for the GTK+ Rezlooks engine. Like I always do, I have compiled support for animation.

[http://www.gnome-look.org/content/show.php?content=39179](http://www.gnome-look.org/content/show.php?content=39179)

I figured I'd post the big there popular engines that are used on the gnome-looks site because there are none for the 64-bit version at least. These packages that I have provided in this and two other posts should perhaps be placed in the Ibex or Jaunty repository. That would rock so many of us.

---

### Post by Pro-reason on 2008-09-11
If you want to contribute packages to the community, start a PPA on Launchpad.

---

### Post by Crafty Kisses on 2008-09-12
Yeah, that's probably the best way. :)

---

### Post by Faolan84 on 2008-09-12
Well I have a launchpad account but I don't see how to place the packages into my PPA repository.

---

### Post by loell on 2008-09-12
you need to activate it. and you also need to package it pseudo formally, if you know  debian packaging that shouldn't be a problem. :)

---

### Post by Pro-reason on 2008-09-12
> **Faolan Devyn Aodfin said:**
> Well I have a launchpad account but I don't see how to place the packages into my PPA repository.

You don't actually place packages there.  You upload the source code, including a directory called “debian” which contains info about the package you want to be created.  Launchpad then compiles and publishes the package.

The documentation is not amazingly good, but I managed to work it out in the end.

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by Faolan84 on 2008-09-12
Compared to Arch, this is way more complicated but I &#314;l give it a try.

---

### Post by dashnu on 2009-10-01
This deb doesnt work anymore with latest beta ubuntu and I still do not see rezlooks in the repoz. "Bad File Descriptor" is the error i get. Any thoughts? Any engines similar to rezlooks I can use in the repoz?

---

### Post by psyke83 on 2009-10-03
> **dashnu said:**
> This deb doesnt work anymore with latest beta ubuntu and I still do not see rezlooks in the repoz. "Bad File Descriptor" is the error i get. Any thoughts? Any engines similar to rezlooks I can use in the repoz?

You resurrected an ancient thread - you probably shouldn't do that for fear of angering the Forum Gods :)

The Rezlooks engine is a very old fork of Clearlooks. the Clearlooks engine itself has advanced much since 2006, and a much superior engine exists in its place - Murrine. Ubuntu's default theme has used the Murrine engine since Hardy, so this engine is installed by default (and therefore most likely on your machine).

See [the homepage]("http://www.cimitan.com/murrine/") for information (but please, keep in mind that it's already installed by default - you don't need to compile it from source yourself).

---

### Post by dannymichel on 2010-04-26
i'd much rather rezlooks than murrine. 
there is no new murrine configurator
has anyone an x64 .deb?

---

### Post by redDEADresolve on 2010-06-13
Even with a 64 bit deb I created from source using checkinstall, rezlooks would work for me in ubuntu 9.10

---

