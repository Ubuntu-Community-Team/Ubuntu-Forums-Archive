---
title: "Installing compilers with no CD or Internet connection"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by cocotu on 2006-09-12
We have a LAMP server downstairs here at work. We were trying to use the ./configure command but we don't have any compilers installed. Right now we are having problems connecting to the Internet due to the Proxy server we are getting this error when we run, [COLOR="RoyalBlue"]apt-get install build-essential[/COLOR]:
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1
  Could no resolve 'RGuisbert@10.0.3.4'

For now I don't have the CD with me, is there a way of downloading these packages using another machine running windows and then install them. If yes, where do I place these packages and how do I install them?

Thanks for your help....

---

### Post by whizbaby on 2006-09-12
Download from here (package according to your hardware, e.g.i386 for a normal PC):
[http://security.ubuntu.com/ubuntu/pool/main/b/binutils/](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/)

switch to the directory you will have it copied to (in terminal) and type

**sudo dpkg -i *name_of_the_package_you_downloaded***

---

### Post by cocotu on 2006-09-12
whizbaby, I got errors:

dpkg: dependency problems prevent configuration of binutils-dev:
binutils-dev depends on binutils (=2.17-1ubuntu1);

I got binutils_2.17-1ubuntu1_386.deb and tried to install it, and I got the same dependency problem, but saying that binutils depends on libc6 (>=2.4-1) however: Version of libc6 on system  is 2.3.60ubuntu20.

What should I do???

---

### Post by whizbaby on 2006-09-13
You are trying to install a package which is too new. When I do *apt-cache search binutils --full* I find this (look at the *version* line)
```

Package: binutils
Priority: optional
Section: devel
Installed-Size: 6848
Maintainer: James Troup <james@nocrew.org>
Architecture: i386
Version: 2.16.1cvs20060117-1ubuntu2.1
Provides: elf-binutils
Depends: libc6 (>= 2.3.4-1)
Suggests: binutils-doc (= 2.16.1cvs20060117-1ubuntu2.1)
Conflicts: gas, elf-binutils, modutils (<< 2.4.19-1)
Filename: pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb
Size: 1406670
MD5sum: 4499747cec6bb1463f7b85144d59f466
Description: The GNU assembler, linker and binary utilities
 The programs in this package are used to assemble, link and manipulate
 binary and object files.  They may be used in conjunction with a compiler
 and various libraries to build programs.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```
So your installed *libc6* should suffice with that.

---

### Post by cocotu on 2006-09-13
So what should I do now??

---

