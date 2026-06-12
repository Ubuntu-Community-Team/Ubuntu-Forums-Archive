---
title: "[SOLVED] what does this error message mean"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-11-10
```
 'pkg-config --modversion glib-2.0' returned 2.14.3, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
```
i wanted to configure gtk+-2.12.1 library which had dependency of glib, atk, pango  etc.  etc.
i make install glib-2.14.3 (the latest version) then while ./configure atk-1.9.1 the above error showed
i think that there was already a lower version of glib present. 
so how can i uninstall the glib-2.12.11 (the older version )
or am i wrong and something else is wrong.

---

### Post by geirha on 2007-11-10
ubuntu allready has a package with glib installed, either (1) you uninstall that package, or (2) you uninstall your own version of glib, and use the one shipped with ubuntu.

alternative 1:
```
aptitude search libglib2
```
uninstall all packages marked with an **i**

alternative 2:
uninstall your glib (sudo make uninstall), then install the glib package ending with -dev
```
aptitude search libglib2
```

---

### Post by rahul_bhise on 2007-11-10
ok so i chosed the second alternative and sudo make uninstall glig-2.14.3
then there was no problem in installing library atk-1.9.1.
but then when installing gtk+-2.12.1 the following error showed
```
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.13.5    atk >= 1.9.0    pango >= 1.17.3    cairo >= 1.2.0) were not met:

Requested 'glib-2.0 >= 2.13.5' but version of GLib is 2.12.11

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
i think now it wants a higher version of glib.
i have downloaded a glib-2.14.3 so now i wanted to upgrade glib-2.12.11 to glib-2.14.3

---

### Post by rahul_bhise on 2007-11-10
anyone on this

---

### Post by rahul_bhise on 2007-11-10
help please

---

### Post by geirha on 2007-11-10
It's a bit odd, since the gtk+ documentation for that version states that it depends on glib 2.12, not 2.13.5. The easiest way of getting gtk+ compiled however, is probably to try an older version, like the latest 2.10 version. 

If you still want gtk+ 2.12.1 you probably need to compile glib yourself, and thinking a bit about it, I don't think you can uninstall ubuntu's glib packages after all, since alot of packages depend on it (and all those would be uninstalled as well). It should work though, to have two versions of glib installed at the same time. You should install your own version of glib in /usr/local/ or your homedir, then when you run ./configure on the gtk+ source, you have to manually specify where it should look for glib, probably with "--with-glib=/usr/local/" as an argument to configure. Read the README and INSTALL files, and run "./configure --help" to get a list of the options you may specify.

Why do you need to compile gtk+ yourself btw?

---

