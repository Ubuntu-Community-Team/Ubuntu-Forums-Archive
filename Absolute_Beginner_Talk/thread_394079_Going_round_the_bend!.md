---
title: "Going round the bend!"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-03-26
Right when I enter ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-hamlib
as per the Install instructions of gMFSK 6 I get this error:-

checking for libgnomeui-2.0 hamlib... Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found
configure: error: Library requirements (libgnomeui-2.0 hamlib) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

So when I install Libgnomeui-2.0 I get this error:-

checking for esound >= 0.2.26 audiofile >= 0.2.3... checking for libgnome-2.0 >= 2.0.0 libgnomecanvas-2.0 >= 2.0.0 libbonoboui-2.0 >= 2.0.0 gconf-2.0 >= 1.1.11... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomecanvas-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomecanvas-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomecanvas-2.0' found Package libbonoboui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libbonoboui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libbonoboui-2.0' found Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (libgnome-2.0 >= 2.0.0 libgnomecanvas-2.0 >= 2.0.0 libbonoboui-2.0 >= 2.0.0 gconf-2.0 >= 1.1.11) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I have install libgnomecanvas-2.0 and gconf-2.0, I get just getting so confused, all I wanted to do was run one simple bit of software!!

This is the reason people give up on Linux

Ian

---

### Post by fakie_flip on 2007-03-26
This guy got it installed using a deb package.
[http://ubuntuforums.org/showthread.php?t=1950&highlight=gMFSK](http://ubuntuforums.org/showthread.php?t=1950&highlight=gMFSK)

This guy is having the same problem as you.
[http://ubuntuforums.org/showthread.php?t=393841&highlight=gMFSK](http://ubuntuforums.org/showthread.php?t=393841&highlight=gMFSK)

---

