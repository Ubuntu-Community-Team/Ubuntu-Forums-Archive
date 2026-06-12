---
title: "get this output when trying to install flash"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by tronnix75 on 2007-10-09
root@jeff-laptop:/home/jeff/Desktop# rpm -Uvh flash-plugin-9.0.48.0-release.i386.rpm
error: Failed dependencies:
        /bin/bash is needed by flash-plugin-9.0.48.0-release.i386
        /bin/sh is needed by flash-plugin-9.0.48.0-release.i386
        libX11.so.6 is needed by flash-plugin-9.0.48.0-release.i386
        libXext.so.6 is needed by flash-plugin-9.0.48.0-release.i386
        libXt.so.6 is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6 is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GCC_3.0) is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GLIBC_2.1) is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GLIBC_2.1.2) is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GLIBC_2.1.3) is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GLIBC_2.2) is needed by flash-plugin-9.0.48.0-release.i386
        libc.so.6(GLIBC_2.3) is needed by flash-plugin-9.0.48.0-release.i386
        libdl.so.2 is needed by flash-plugin-9.0.48.0-release.i386
        libdl.so.2(GLIBC_2.0) is needed by flash-plugin-9.0.48.0-release.i386
        libdl.so.2(GLIBC_2.1) is needed by flash-plugin-9.0.48.0-release.i386
        libfontconfig.so.1 is needed by flash-plugin-9.0.48.0-release.i386
        libfreetype.so.6 is needed by flash-plugin-9.0.48.0-release.i386
        libglib-2.0.so.0 is needed by flash-plugin-9.0.48.0-release.i386
        libgobject-2.0.so.0 is needed by flash-plugin-9.0.48.0-release.i386
        libgtk-x11-2.0.so.0 is needed by flash-plugin-9.0.48.0-release.i386
        libm.so.6 is needed by flash-plugin-9.0.48.0-release.i386
        libm.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.48.0-release.i386
        libpthread.so.0 is needed by flash-plugin-9.0.48.0-release.i386
        libpthread.so.0(GLIBC_2.0) is needed by flash-plugin-9.0.48.0-release.i386
        libpthread.so.0(GLIBC_2.1) is needed by flash-plugin-9.0.48.0-release.i386
        libpthread.so.0(GLIBC_2.2) is needed by flash-plugin-9.0.48.0-release.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by flash-plugin-9.0.48.0-release.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by flash-plugin-9.0.48.0-release.i386


i installed Yum and RPM what now?

---

### Post by tito2502 on 2007-10-09
Is there any reason you are using RPMs?

You can go to system > administration > software sources

Enable the restricted repository

Then you can run

sudo apt-get install flashplugin-nonfree

---

### Post by skymera on 2007-10-09
why RPM?

get the tarball

[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

---

### Post by rsambuca on 2007-10-09
You do know this is the Ubuntu forums, right? ;)

Ubuntu generally uses apt-get to install deb files, since it is a debian based system.

Anyways, to install flash, make sure your universe and multiverse repositories are enabled and then```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tronnix75 on 2007-10-09
> **rsambuca said:**
> You do know this is the Ubuntu forums, right? ;)

Ubuntu generally uses apt-get to install deb files, since it is a debian based system.

Anyways, to install flash, make sure your universe and multiverse repositories are enabled and then```
sudo apt-get install ubuntu-restricted-extras
```

WHAT? univers and multi verse?? 

i ran that command what does it do?:confused:

---

### Post by tronnix75 on 2007-10-09
> **tito2502 said:**
> Is there any reason you are using RPMs?

You can go to system > administration > software sources

Enable the restricted repository

Then you can run

sudo apt-get install flashplugin-nonfree

yes because i dont know what im doing NEWB:

so i dont need to install RPM?

how do i uniinstall it?

do i need to install YUM?

---

### Post by rsambuca on 2007-10-09
> **tronnix75 said:**
> WHAT? univers and multi verse?? 

i ran that command what does it do?:confused:

Go to "System - Administration - Software Sources" from the top menu.  Make sure you enable the multiverse and universe repositories.  Update your sources when prompted.

Then enter the code I gave you earlier```
sudo apt-get install ubuntu-restricted-extras
```This will install flash, java, msttcorefonts, and multimedia codecs.

---

### Post by tronnix75 on 2007-10-09
> **rsambuca said:**
> Go to "System - Administration - Software Sources" from the top menu.  Make sure you enable the multiverse and universe repositories.  Update your sources when prompted.

Then enter the code I gave you earlier```
sudo apt-get install ubuntu-restricted-extras
```This will install flash, java, msttcorefonts, and multimedia codecs.

do i need to uninstall YUM or RPM?:confused:

---

### Post by rsambuca on 2007-10-09
It's up to you.  They aren't going to hurt anything if you just leave them, or if you wish you can uninstall them.

---

