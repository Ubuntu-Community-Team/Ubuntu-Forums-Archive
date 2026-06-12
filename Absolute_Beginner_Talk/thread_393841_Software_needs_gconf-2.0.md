---
title: "Software needs gconf-2.0"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-03-26
I am trying to install gMFSK but when I do ./configure I get this error 

checking for esound >= 0.2.26 audiofile >= 0.2.3... checking for libgnome-2.0 >= 2.0.0 libgnomecanvas-2.0 >= 2.0.0 libbonoboui-2.0 >= 2.0.0 gconf-2.0 >= 1.1.11... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomecanvas-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomecanvas-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomecanvas-2.0' found Package libbonoboui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libbonoboui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libbonoboui-2.0' found Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (libgnome-2.0 >= 2.0.0 libgnomecanvas-2.0 >= 2.0.0 libbonoboui-2.0 >= 2.0.0 gconf-2.0 >= 1.1.11) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I have installed libgnomecanvas-2.0, any ideas??

Ian

---

### Post by zvacet on 2007-03-26
See this page
[http://packages.ubuntu.com/edgy/libs/libgnome-desktop-2]("http://packages.ubuntu.com/edgy/libs/libgnome-desktop-2")

---

