---
title: "problems compiling libtorrent/rtorrent(debian)"
date: 2011-10-26
forum: Any Other OS
---

### Post by jargs on 2011-10-26
hello there, can i please ask which linux distribution is recommended for compiling and installing the latest version of rtorrent? I have tried debian 5, which did not work do to errors, debian 6 does not work do to errors, and also centos 5 does not work do to errors.

here is a sample of the error message when using "./configure" 

> ./configure: line 3209: syntax error near unexpected token `1.9.6'
./configure: line 3209: `AM_PATH_CPPUNIT(1.9.6)'"

and yes i have googled the error message and installed libcppunit-dev and it still does not work...

any help is much appreciated, thanks.

---

### Post by crazy bird on 2011-10-26
Just a question: why compiling a torrent program since there are already a couple torrent programs in the repositories?

---

### Post by jargs on 2011-10-26
because i would like the latest version

ok nevermind close this thread.

---

### Post by crazy bird on 2011-10-26
That's a reasonable reason. But then look for a torrent program whch has a .deb package file. Then you won't have to compile a program. Just double click and get it installed using GDebi.

---

### Post by oldos2er on 2011-10-26
Moved to Other OS/Distro Talk.

---

### Post by andrew.46 on 2011-10-27
I have just finished compiling rtorrent on *Slackware 13.37* without any problem. I assume you have compiled libsig++ (I used 2.2.7), libtorrent 0.12.9 and rtorrent 0.8.9 in that order? Unfortunately I have no great insights into the build environment of Debian :(. Details of the Slackware build here:

[http://slackbuilds.org/repository/13.37/libraries/libsigc++/](http://slackbuilds.org/repository/13.37/libraries/libsigc++/)
[http://slackbuilds.org/repository/13.37/libraries/libtorrent/](http://slackbuilds.org/repository/13.37/libraries/libtorrent/)
[http://slackbuilds.org/repository/13.37/network/rtorrent/](http://slackbuilds.org/repository/13.37/network/rtorrent/)

---

