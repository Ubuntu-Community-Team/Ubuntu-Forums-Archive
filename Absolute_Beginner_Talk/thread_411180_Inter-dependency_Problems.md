---
title: "Inter-dependency Problems"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Frederick J. Harris on 2007-04-16
What does one do if you have two packages, e.g., pkg1 and pkg2, and when you try to install pkg1 you are told you have to install pkg2 first, and then when you try that you are told you have to install pkg1 first?  Here is the Terminal output where I am trying to install the build-essential package, which package contains around 40 dependent packages.  Most have gone in OK but a few I'm stuck on.  I have to do this because I have no connection on the computer with Ubuntu, so I have to get the package installed manually.  The problem packages are the g++-4.1 compiler and the libstdc++6-4.1 libraries...

 fredharris@CODEWARRIOR:~/DebPkgs$ sudo dpkg -i g++-4.1_4.1.1-13ubuntu5_i386.deb
(Reading database ... 90671 files and directories currently installed.)
Preparing to replace g++-4.1 4.1.1-13ubuntu5 (using g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Unpacking replacement g++-4.1 ...
dpkg: dependency problems prevent configuration of g++-4.1:
 g++-4.1 depends on libstdc++6-4.1-dev (= 4.1.1-13ubuntu5); however:
  Package libstdc++6-4.1-dev is not configured yet.
dpkg: error processing g++-4.1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-4.1

fredharris@CODEWARRIOR:~/DebPkgs$ sudo dpkg -i libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb
(Reading database ... 90671 files and directories currently installed.)
Preparing to replace libstdc++6-4.1-dev 4.1.1-13ubuntu5 (using libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Unpacking replacement libstdc++6-4.1-dev ...
dpkg: dependency problems prevent configuration of libstdc++6-4.1-dev:
 libstdc++6-4.1-dev depends on g++-4.1 (= 4.1.1-13ubuntu5); however:
  Package g++-4.1 is not configured yet.
dpkg: error processing libstdc++6-4.1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++6-4.1-dev

---

### Post by zvacet on 2007-04-16
Both of your packages have their own dependencies.You need them all if you want to install.I belive you are familyare with this page
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by choben on 2008-04-03
I have the same problem...
That response doesn't seem to address it though, as the problem is mutual dependency of two packages.
So atleast one other person has this problem!:confused:

---

### Post by kpkeerthi on 2008-04-03
> **Frederick J. Harris said:**
> What does one do if you have two packages, e.g., pkg1 and pkg2, and when you try to install pkg1 you are told you have to install pkg2 first, and then when you try that you are told you have to install pkg1 first?  Here is the Terminal output where I am trying to install the build-essential package, which package contains around 40 dependent packages.  Most have gone in OK but a few I'm stuck on.  I have to do this because I have no connection on the computer with Ubuntu, so I have to get the package installed manually.  The problem packages are the g++-4.1 compiler and the libstdc++6-4.1 libraries...

If you are sure that you got all the dependent packages in ~/DebPkgs, just do
```
sudo dpkg -i *.deb
``` from inside DebPkgs folder.

---

### Post by zvacet on 2008-04-03
```
sudo apt-get install pkg1 pkg2
```

---

### Post by Tim Legg on 2008-04-06
I reproduced this on my Debian etch box and fixed it with 

dpkg -i g++-4.1_4.1.1-13ubuntu5_i386.deb libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb

whenever I have odd interdependencies or recursive dependencies, I install all the other dependent packages first and then do the pair like you see above.  dpkg is smart enough to figure it out.

---

