---
title: "Installing Canon Pixma ip1500 Printers"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by darkchest on 2007-02-28
I have a Canon Pixma ip1500 Printer and it is connected to an AMD 64 computer.  I have tried other post, but i dont seem to find the drivers for AMD 64 and sometimes i dont even see the drivers.

Could anyone pls help.

---

### Post by geekgod on 2007-02-28
[http://software.canon-europe.com/software/0022415.asp?model=](http://software.canon-europe.com/software/0022415.asp?model=)

You can try the above link, since its a source package it shouldnt matter what processor you use as it will build for your system

---

### Post by darkchest on 2007-02-28
after installing, i tried using sudo alien *i386.rpm, and this is the error i got.

signax@Signax:~/Desktop/iP1500$ sudo alien *i386.rpm
Password:
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/bjfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find path for libcups.so.2
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared librar y libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared librar y libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared librar y libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared librar y libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libcups.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared librar y libcups (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared librar y libpopt (soname 0, path /lib32/libpopt.so.0, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in pack age's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: bjfilter-common-2.50: No such file or directory

---

### Post by mr_niceguy on 2007-03-15
Drivers via apt:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

---

