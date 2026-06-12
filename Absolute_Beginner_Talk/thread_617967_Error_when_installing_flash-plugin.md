---
title: "Error when installing flash-plugin"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by aafont70 on 2007-11-19
Hi,

I get the following error when trying to install flash-plugin:

root@linux-laptop:~# rpm -Uvh flash-plugin-9.0.48.0-release.i386.rpm 
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

Any ideas???

Thanks.

---

### Post by taurus on 2007-11-19
Flash plugin is available from repos.

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by ericartman on 2007-11-19
I highly recommend "ubackup" it does many amazing things for us newbies. Just do a forum search.

Cart

---

### Post by rsambuca on 2007-11-20
> **ericartman said:**
> I highly recommend "ubackup" it does many amazing things for us newbies. Just do a forum search.

Cart

What does that have to do with installing flash?

---

### Post by ericartman on 2007-11-23
Get more questions about this . It (ubackup) is a program for installing codecs for dvd playing and flash and other things including, you guessed it, Backups! lol Anyway if you just search in the forums for Ubackup and read the page it will explain . The name is confusing but it is an awesome program.I use it, with much success.

cart

---

### Post by xeth_delta on 2007-11-23
> **aafont70 said:**
> Hi,

I get the following error when trying to install flash-plugin:

root@linux-laptop:~# rpm -Uvh flash-plugin-9.0.48.0-release.i386.rpm 
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

Any ideas???

Thanks.

Are you using an Ubuntu based distribution? If so, you don't need to install **rpm** packages, but **deb** ones. Anyway, most of the programs can be found in the repositories.

You can look for programs using graphical interfaces to the package management system, for instance, synaptic (ubuntu), or adept (kubuntu).

If you want to use the command line:
```
sudo aptitude
```
or to search directly
```
aptitude search package_name
```
and to install
```
sudo aptitude install package_name
```
or
```
sudo apt-get install package_name
```

Xeth

---

### Post by Soft_Taco on 2007-11-24
I originally had this problem while installing it in Firefox.

I turned of the 'ubuntu' add-on in my add-ons, then installed with no problems.

I then just turned it back on, and it worked.:)

---

