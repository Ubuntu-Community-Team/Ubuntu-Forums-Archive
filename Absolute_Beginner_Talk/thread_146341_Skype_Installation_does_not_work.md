---
title: "Skype Installation does not work?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by pyrro on 2006-03-18
Help!

I am very new with LInux and just installed the Ubuntu LInux 5.10 into my comp. 
I have tried to install Skype into Ubuntu with the instructions given in Wiki for Skype Installation, but I seem to fail still...Can anyone help?

Following is the installation log...So everything seems to well until command:
sudo alien skype-1.2.0.18-fc3.i586.rpm

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/skype
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libXss.so.1
dpkg-shlibdeps: warning: could not find path for libqt-mt.so.3
dpkg-shlibdeps: warning: could not find any packages for  (libXss.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXss (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libqt-mt.so.3)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libqt-mt (soname 3, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: skype-1.2.0.18: No such file or directory

---

### Post by cjjb on 2006-03-18
[QUOTE=pyrro]
sh: gcc: command not found
[/QUOTE]

That looks like your main problem, try:

```
sudo apt-get install build-essential
```

then restart the skype install.

---

### Post by pyrro on 2006-03-18
Thanks, but it seems not be the solution. Still fails similarly...

Now I just noticed one issue. I have 64-bit version of the Ubuntu...That may be the problem I guess? I there are 64-bit version available...

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/skype
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libXss.so.1
dpkg-shlibdeps: warning: could not find path for libqt-mt.so.3
dpkg-shlibdeps: warning: could not find any packages for  (libXss.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXss (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libqt-mt.so.3)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libqt-mt (soname 3, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: skype-1.2.0.18: No such file or directory

---

### Post by e2k on 2006-03-18
Did you read this howto [https://wiki.ubuntu.com/Skype?highlight=%28skype%29]("https://wiki.ubuntu.com/Skype?highlight=%28skype%29") ?
The deb package seems to have been fixed, I'd try that out if I were you :)

---

