---
title: "Confused by Jpackage"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by bckirkup on 2007-06-04
Jpackage... well, I need to install all sorts of things; ok... jedit and jalview... and they are in jpackage repositories.  I don't trust all sorts of dependencies in the outside world of linux.  I've seen too much linux to think I can sort it out.  So, I want to use a package manager to do the installations.

But jpackage talks about vendors.list and I can't find one.  And mirrors for other things, but not Ubuntu.  

Can someone give this dufus the step by step on how to get from point a to point b?

Thanks.

---

### Post by bckirkup on 2007-06-12
Still nothing after a week?

---

### Post by vadania on 2007-08-05
I'm having problems with installing Jpackage, too.
I had followed the instructions from [http://jpackage.org/installation.php]("http://jpackage.org/installation.php")
I run Ubuntu 7.04 Feisty Fawn.
I have sun-java5-jdk     1.5.0-11-1ubuntu2, sun-java5-jre  1.5.0-11-1ubuntu2 
I have Installed 'jpackage-utils'

My problems start with installing java-1.5.0-sun-compat (which is requiered for JVM provided by Sun). 
This package was downloaded as a RPM and then converted to .deb with alien.

Here is the error report I get:
[I]$ sudo gdebi /home/bogdan/Desktop/java-1.5.0-sun-compat_1.5.0.11-2_i386.deb 
Reading package lists: Done

JPackage Java compatibility package for Sun's JDK
 This package provides JPackage compatibility symlinks and directories
 for the vendor's JDK rpm.

 (Converted from a rpm package by alien version 8.65.)
Do you want to install the software package? [y/N]:y
(Reading database ... 313396 files and directories currently installed.)
Unpacking java-1.5.0-sun-compat (from .../java-1.5.0-sun-compat_1.5.0.11-2_i386.deb) ...
dpkg: error processing /home/bogdan/Desktop/java-1.5.0-sun-compat_1.5.0.11-2_i386.deb (--install):
 trying to overwrite `/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/COPYRIGHT', which is also in package sun-java5-jdk[/I]

There are probably more inconsistencies in this package. How should I deal with this and the others?
Can't Canonical collaborate with the JPackage.org team to make it easier for people to install java applications?

---

### Post by AlexenderReez on 2007-08-05
i guess it is a matter of can't overwrite copyright isn't it?you can try force overwrite it..

>  sudo dpkg --force-overwrite -i <package.deb>

---

