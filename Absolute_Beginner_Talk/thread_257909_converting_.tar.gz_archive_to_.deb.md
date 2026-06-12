---
title: "converting .tar.gz archive to .deb"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by rajeshgovindan on 2006-09-15
what is the command to convert a tar.gz archive into .deb ?
please explain in depth

thanx in advance

Rajesh

---

### Post by jrib on 2006-09-15
[https://help.ubuntu.com/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/ubuntu/packagingguide/C/index.html) be sure to check the references in the appendix too

---

### Post by daller on 2006-09-15
or this:

[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)

---

### Post by 3rdalbum on 2006-09-15
It depends what you want to do - do you want to compile the source code into a full-featured .deb package for distributing? Or do you just want to create a .deb package so it would be easy to remove later?

If the former, then follow the instructions above. If you just want something for your personal use, then follow these instructions:

1. Download the Checkinstall package (sudo apt-get install checkinstall) and, if you haven't already got it, download build-essential (sudo apt-get install build-essential). You only need to download them this once.

2. Follow the instructions given in the "INSTALL" file inside the .tar.gz archive, but INSTEAD of doing "make install", do "sudo checkinstall".

3. Follow the prompts and use the default settings for everything.

4. At the end, you will have a Debian package inside the same directory as the source code, and this package will be installed automatically for you. Enjoy.

---

### Post by Metacarpal on 2006-09-15
> **3rdalbum said:**
> It depends what you want to do - do you want to compile the source code into a full-featured .deb package for distributing? Or do you just want to create a .deb package so it would be easy to remove later?

If the former, then follow the instructions above. If you just want something for your personal use, then follow these instructions:

1. Download the Checkinstall package (sudo apt-get install checkinstall) and, if you haven't already got it, download build-essential (sudo apt-get install build-essential). You only need to download them this once.

2. Follow the instructions given in the "INSTALL" file inside the .tar.gz archive, but INSTEAD of doing "make install", do "sudo checkinstall".

3. Follow the prompts and use the default settings for everything.

4. At the end, you will have a Debian package inside the same directory as the source code, and this package will be installed automatically for you. Enjoy.

I only recently discovered checkinstall, but I freaking love it.

---

