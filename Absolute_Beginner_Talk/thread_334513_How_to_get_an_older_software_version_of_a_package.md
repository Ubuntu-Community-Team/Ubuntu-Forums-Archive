---
title: "How to get an older software version of a package?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Master One on 2007-01-09
I'd like to install an older version of mldonkey-server than the one which is in the edgy repos.

In Gentoo this task is very easy, because you usually have the ebuilds of privious versions in portage, but for a binary distribution it's about the ready to use deb package of course.

So is there any possibility to find older deb package, or do I have to build from source?

---

### Post by Titus A Duxass on 2007-01-09
I do this when I want an old version of mysql-server:

sudo apt-get install mysql-server-4.1

using just mysql-server installs version 5.

Maybe you can adapt this for your needs.

See what is available with apt-cache search mldonkey.

---

### Post by deadgobby on 2007-01-09
Go to
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
or here the other search link Debian
[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=mysql&searchon=names&subword=1&version=stable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=mysql&searchon=names&subword=1&version=stable&release=all)

---

### Post by Master One on 2007-01-09
Already tried the debian package search and played around with apt-cache, but no older versions of the desired package was found. Specifically I was looking for mldonkey-server-2.7.3

Any more suggestions?

I took a look at the mldonkey sourceforge archive, and besides the source there is the following ready to use version available:

mldonkey-2.7.3.static.i386-Linux_glibc-2.3.2.tar.bz2

The question for this one is: Which glibc version is used in Edgy, how do I check this, and what if Edgy has a different glibc?

---

### Post by webmusic on 2007-03-10
So, in other words, I could install MySQL 3.23.58 if needed? The software we are running requires this version. Can't use anything above it. Also Apache 1.3, and PHP 4.4.4 would be good to install.....

Is this something that would need to be done after the initial install?

---

