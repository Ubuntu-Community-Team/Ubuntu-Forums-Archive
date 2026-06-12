---
title: "gcc error while trying to install Java runtime"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by noob12345 on 2007-05-02
I'm following instructions to install JRE:
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

but got this:

owner@owner-desktop:~$ fakeroot make-jpkg jre-6u1-linux-i586.rpm
Creating temporary directory: /tmp/make-jpkg.XXXXkHsXxN
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done


someone please tell me how do i solve this, i don't even know what to google
i think I'm just missing a package or two, but don't know which:confused:

---

### Post by oilchangeguy on 2007-05-02
use automatix see [www.getautomatix.com](www.getautomatix.com) click on the installition tab, locate the easy install for 6.06, and install it. automatix automates the installation of alot of software.

---

### Post by bobplano on 2007-05-02
well firstly it is an rpm package and uibuntu uses deb packages so you might need to use alien if there is no deb package(but i think there is). make sure you have gcc and make sure it is up to date. (gcc -v and the version should be something like 4.1 or something). if you use automatix im sure someone will warn you that it will bork your system but i havent experienced any problems

---

### Post by zvacet on 2007-05-03
If you have all repositories open,you will find Java in synaptic.In search box type **sun** and install bin package.

---

### Post by noob12345 on 2007-05-03
thank you, I had no idea there were extra repositories

---

