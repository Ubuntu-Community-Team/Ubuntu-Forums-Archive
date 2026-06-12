---
title: "Uninstalling programs"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-06
I understand *apt-get --purge remove* does a clean and complete uninstall of a package. However, this is only for packages that were installed using *apt-get* and packages that show up with *dpkg -l*

So how do I do a complete removal of a package that I installed from source? I mean, the *./configure*,*make*,*make install* method? How do I know what files it created and where it saved them? 

Simply put, how do I *purge* a package that I compiled from the source? 

The reason I want to know is that I often install packages just to test, and then purge them completely once I don't find a need for them. 

Thanks !

---

### Post by amohanty on 2005-12-06
Redo the install with checkinstall. so instead of:

```

./configure
make
sudo make install

```

do a:

```

./configure
make
sudo checkinstall

```

This creates a .deb and installs it so that its available to remove via dpkg.
So if you use the same source tarball, it will install all the files to the same location and then you can use the purge option.

To install checkinstall enable universe repos and 
```
sudo apt-get install checkinstall
```

HTH
AM

---

### Post by harisund on 2005-12-06
Wow ! That was a quick reply, and indeed a very helpful one.

Thanks a lot !

---

### Post by mihaic on 2005-12-07
I am also new to apt packaging, and as a matter of fact to Linux and seeing how easy it is to install something on Ubuntu, one soon wanders "how do I uninstall things?" and this is indeed an good answer. 

Thanks,
Mihai

---

### Post by deNoobius on 2005-12-07
So, could one set up an alias so that install = checkinstall for every install, so you have the ability to easily uninstall anything? Or would that cause other problems?

---

### Post by SuSUntu on 2005-12-07
I've used "checkinstall" for a while, both on Suse 64-bit and Ubuntu 64-bit.

Checkinstall, for whatever reasons, fails quite often (more often on Ubuntu for me) to successfully create a package, and I am forced to use the standard "make install" (which does work in those cases where "checkinstall" fails). As a result, many of my source-code installations are not packaged for easy uninstalling.

I recently found an app called Paco which works as a tracking tool creating text files of all the changes to your system related to the installation of any source code. I almost prefer it to "checkinstall" now because it never fails (if "make install" works, so will Paco ... the same can't always be said of "checkinstall").

The best usage would be:

- ./configure
- make
- checkinstall -D
- if checkinstall fails, paco -lp nameofapp-1.0 "make install", which will create a text file detailing system changes which can be referred to when a need to completely uninstall the software arises.

[http://paco.sourceforge.net/index.html](http://paco.sourceforge.net/index.html)

From Paco man:

DESCRIPTION
       Paco  is  a  program to aid package management when installing packages
       from source code.

       When installing a package, paco can be used in log  mode  (with  option
       -l) to wrap the installation command (e.g. "make install"), and log the
       created  files.  By  default   the   log   is   stored   in   directory
       '/var/log/paco'.
       Paco gets also some extended information about the package that is bee-
       ing installed (version, author, description, configure options...), and
       stores it into a log in directory '/var/log/paco/_info'.

       Once  some packages are installed and properly logged, paco can be used
       in list mode, which is the default,  to  display  package  information.
       Several options are provided to print the information in different for-
       mats.

       There are also options to remove  packages,  query  for  the  owner  of
       files, or maintain the package database.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

---

