---
title: "kiba-dock checkinstall problem"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by bchan90 on 2007-03-19
i am following the how to on these forums and i'm at the "sudo checkinstall" step.

but i always run into this error:

> ========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/bchan90/kiba-dock/akamaru/src'
make[2]: Entering directory `/home/bchan90/kiba-dock/akamaru/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libakamaru.la' '/usr/local/lib/libakamaru.la'
/usr/bin/install -c .libs/libakamaru.so.0.0.0 /usr/local/lib/libakamaru.so.0.0.0
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so.0 || { rm -f libakamaru.so.0 && ln -s libakamaru.so.0.0.0 libakamaru.so.0; }; })
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so || { rm -f libakamaru.so && ln -s libakamaru.so.0.0.0 libakamaru.so; }; })
/usr/bin/install -c .libs/libakamaru.lai /usr/local/lib/libakamaru.la
/usr/bin/install -c .libs/libakamaru.a /usr/local/lib/libakamaru.a
chmod 644 /usr/local/lib/libakamaru.a
ranlib /usr/local/lib/libakamaru.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bchan90/kiba-dock/akamaru/src'
make[1]: Leaving directory `/home/bchan90/kiba-dock/akamaru/src'
Making install in include
make[1]: Entering directory `/home/bchan90/kiba-dock/akamaru/include'
make[2]: Entering directory `/home/bchan90/kiba-dock/akamaru/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/akamaru" || mkdir -p -- "/usr/local/include/akamaru"
 /usr/bin/install -c -m 644 'akamaru.h' '/usr/local/include/akamaru/akamaru.h'
make[2]: Leaving directory `/home/bchan90/kiba-dock/akamaru/include'
make[1]: Leaving directory `/home/bchan90/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/bchan90/kiba-dock/akamaru'
make[2]: Entering directory `/home/bchan90/kiba-dock/akamaru'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'akamaru.pc' '/usr/lib/pkgconfig/akamaru.pc'
make[2]: Leaving directory `/home/bchan90/kiba-dock/akamaru'
make[1]: Leaving directory `/home/bchan90/kiba-dock/akamaru'

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./COPYING
./ChangeLog
./INSTALL
./NEWS
./README
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru/AUTHORS': Operation not permitted
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru/COPYING': Operation not permitted
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru/ChangeLog': Operation not permitted
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru/INSTALL': Operation not permitted
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru/NEWS': Operation not permitted
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru/README': Operation not permitted
chown: changing ownership of `/var/tmp/YMDKNHMGrCaELlGcRLVbo/package//usr/share/doc/akamaru': Operation not permitted

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package


i realize a lot of other people have run into this problem but i've tried to do what they've posted (usually this means changed the Release number to "1" but this didn't change anything.  any help or suggestions would be greatly appreciated.

---

### Post by Kobalt on 2007-03-20
I remember having bloged about kiba once a while ago, and there was a .deb package available, here it is : [http://ubunteros.free.fr/kiba-dock_0.1-1_i386.deb](http://ubunteros.free.fr/kiba-dock_0.1-1_i386.deb)
You need to download & install the package then download this [kiba.schema]("http://ubunteros.free.fr/kiba.schemas") file, and run this command : ```
gconftool-2 &#8211;install-schema-file=*path_to_kiba.schemas*
```

ANd should be able tu run kiba with the command 'dock' .

---

### Post by bchan90 on 2007-03-20
that did the trick!:)   thanks for the help

---

