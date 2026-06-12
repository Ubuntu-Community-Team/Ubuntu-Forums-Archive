---
title: "Dependency is not satisfiable: libc6 and libgmime2.1"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by lucat on 2007-10-10
Hi,
I have tried to install  minicom package  (minicom_2.2-5_i386.deb) on a Toshiba 4030 Satellite equipped with the  xubuntu-6.06.1-alternate-i386.iso version installed, but when I tried to unpackage  it, the Package installer wrote:
Dependency is not satisfiable: libc6 . How can I run the minicom?

Then I tried to install the tracker_0.5.4_i386.deb package and the Package installer wrote: 
Dependency is not satisfiable: libgmime2.1. How can I run Tracker application?

---

### Post by zvacet on 2007-10-10
[libc6]("libc6")

Be sure to install dependencies first(mark with red ball and blue ones).


[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgmime2.1.&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgmime2.1.&searchon=names&subword=1&version=dapper&release=all")

---

### Post by lucat on 2007-10-10
I have installed the libc6 but I get the same error. Do you have minicom installed on your machine?

I have installed libgmime2.1, but I got another "Dependency is not satisfiable" for another kind of packet

---

### Post by Kilz on 2007-10-10
Its possible that the package requires a newer version of those libraries. Dapper (6.06) is starting to get old, you might want to consider an upgrade. Gutsy will be released on the 18th. That would be an upgrade of 3 versions.

---

### Post by lucat on 2007-10-10
thanks Kilz. anyhow do you have installed minicom on your PC?

---

### Post by lucat on 2007-10-10
I solved the problem.
I issued the command sudo dpkg -i minicom_2.2-5_i386.deb and I got the answer:
...dependency problems...
minicom depends on libc6 (>=2.5-0ubuntu1) however: Version of libc6 on system is 2.3.6-0ubuntu20

So I downloaded the package libc6_2.5-0ubuntu14_i386.deb

from the following link:

 [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-0ubuntu14_i386.deb&md5sum=93f5e50c41abfaeac5963a448b9881e0&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-0ubuntu14_i386.deb&md5sum=93f5e50c41abfaeac5963a448b9881e0&arch=i386&type=main)

and then I have installed it.
Finally I have issued the command apt-get -f install and then minicom works!

---

