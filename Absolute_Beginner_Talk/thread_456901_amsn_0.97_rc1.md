---
title: "amsn 0.97 rc1"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-05-28
i tried to install but got the following:

```
# Preparing package: AMSN MSN client                                            
# Checking for required C library versions ... failed
# FAIL: 
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
# 
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
# 
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL: Unable to prepare package AMSN MSN client.
Press ENTER to exit.


```

---

### Post by AlanR8 on 2007-05-28
Try installing it from Automatix...worked for me

---

### Post by starcraft.man on 2007-05-28
No... Automatix is certainly _NOT_ needed to install aMSN, or any other program for that matter. >.>

I assume you were aiming for the latest build, [this is it ]("http://ubuntuforums.org/showthread.php?t=416062&highlight=new+aMSN")as far as I know, download the 4 debs at the top and scroll down till you see a post with two more debs, download the second. Then install all 5 in the right order (they depend on each other and will tell you when they can install).

It is a great new look compared to the old aMSN :).

---

### Post by supersonicdarky on 2007-05-28
:(

```
kernel@laptop:~/downloaded$ sudo dpkg -i --force-architecture *.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 179274 files and directories currently installed.)
Preparing to replace amsn 0.97-0+svn20070418~3v1ubuntu0 (using amsn_0.97-0+svn20070418~3v1ubuntu0_i386.deb) ...
Unpacking replacement amsn ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace tcl8.5 8.5.0.a5-3v1ubuntu0 (using tcl8.5_8.5.0.a5-3v1ubuntu0_i386.deb) ...
Unpacking replacement tcl8.5 ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace tcltls 1.5.0-3~neto1-3v1ubuntu0 (using tcltls_1.5.0-3~neto1-3v1ubuntu0_i386.deb) ...
Unpacking replacement tcltls ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace tile 0.7.8-3v1ubuntu0 (using tile_0.7.8-3v1ubuntu0_i386.deb) ...
Unpacking replacement tile ...
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Preparing to replace tk8.5 8.5.0.a5-3v1ubuntu0 (using tk8.5_8.5.0.a5-3v1ubuntu0_i386.deb) ...
Unpacking replacement tk8.5 ...
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tcllib (>= 1.8); however:
  Package tcllib is not installed.
 amsn depends on libsnack2 (>= 2.2.9); however:
  Package libsnack2 is not installed.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Setting up tcl8.5 (8.5.0.a5-3v1ubuntu0) ...

Setting up tcltls (1.5.0-3~neto1-3v1ubuntu0) ...

Setting up tk8.5 (8.5.0.a5-3v1ubuntu0) ...

Setting up tile (0.7.8-3v1ubuntu0) ...
Errors were encountered while processing:
 amsn

```

(i have all the packages in there. installing one by one doesnt work either.)

---

### Post by arnieboy on 2007-05-28
> **starcraft.man said:**
> I assume you were aiming for the latest build, [this is it ]("http://ubuntuforums.org/showthread.php?t=416062&highlight=new+aMSN")as far as I know, download the 4 debs at the top and scroll down till you see a post with two more debs, download the second. Then install all 5 in the right order (they depend on each other and will tell you when they can install)..
Those packages will do an extremely good job of breaking the next Ubuntu upgrade. I do hope you are aware of that and why that is so.

---

### Post by p0g0 on 2007-06-12
Works flawlessly for me :KS

---

### Post by Crafty Kisses on 2007-06-12
> **p0g0 said:**
> Works flawlessly for me :KS

Haha, best post all day. :popcorn:

---

