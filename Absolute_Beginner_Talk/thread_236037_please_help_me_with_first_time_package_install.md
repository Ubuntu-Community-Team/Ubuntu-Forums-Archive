---
title: "please help me with first time package install"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by camelgrass on 2006-08-14
I want to install Opera on 6.06. I have downloaded the tar.gz file but can't work out how to install it with Add/Remove.

What's the difference between the .deb and tar.gz packages?

Thanks for your help!

Marty

---

### Post by Perfect Storm on 2006-08-14
Short version:
.deb are debian package files (which Ubuntu also uses) that make it easy to install on Debian based systems.

tar.gz packages are not nesserally a package to install tar.gz is compressed files. It can be every thing from pictures to documents (like the .zip for windows). But in this case they might contain source codes (doubly afterall Opera isn't GPL), but it could also be dynamic binaries.

If you want to install Opera I suggest you add this to your sourcelist: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Want to know how check here: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Usually on Ubuntu you don't download from diffrent pages but have a central place to download from. Check synaptic package manager (System ---> Adminstration).

---

### Post by Pawka on 2006-08-14
Tar.gz is an archive, deb - binary package. Download Opera .deb package, then run console and type this:


cd path/where/opera.deb/is
sudo dpkg -i opera.deb


In this example you should change "opera.deb" to your downloaded .deb file name :-)

---

