---
title: "Upgrading the Boost Library..."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-08-06
I currently have Boost version 1.33 but need to upgrade to version 1.34.

Whats the best way of doing this?

The Boost source debian package is listed at [http://packages.qa.debian.org/b/boost.html](http://packages.qa.debian.org/b/boost.html)

---

### Post by Pragmatist on 2007-08-06
I'm assuming it is a **.deb **file.  In that case, you can download the .deb file and use a program called "gdebi" to install it.  First install gdebi from the repositories.To quote from the package description, **gdebi**
> lets you install local deb packages resolving and installing
its dependencies. apt does the same, but only for remote (http, ftp)
located packages.

---

### Post by B-777 on 2007-08-06
> **Pragmatist said:**
> I'm assuming it is a **.deb **file.  In that case, you can download the .deb file and use a program called "gdebi" to install it.  First install gdebi from the repositories.To quote from the package description, **gdebi**

I have gdebi installed, but if you take a look at the source section towards the bottom, it lists 3 different tar.gz files: 

    * boost_1.34.0-1.dsc
    * boost_1.34.0.orig.tar.gz
    * boost_1.34.0-1.diff.gz

There is no debian package listed, so I assume I will have to manually compile the package, which I have no idea how to do or what package to download from the above. 

If anyone else has any ideas...please do share them :D

---

### Post by Pragmatist on 2007-08-06
According to this post:
[http://ubuntuforums.org/showthread.php?t=139322](http://ubuntuforums.org/showthread.php?t=139322)

you can use "checkinstall" instead of "make install" and the output will be a .deb file.  Then you can use gdebi with the .deb

Here is the procedure for a .tar.gz that has source code that needs compiling, is:
Unpack the tarball:
```
tar xvzf packagename.tar.gz
```Switch into the directory that the above command created and type these commands in order:

```
./configure
``````
make
``````
checkinstall
```

---

