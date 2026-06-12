---
title: "eclipse on a eMac"
date: 2005-09-19
forum: Apple PPC Users
---

### Post by freemanen on 2005-09-19
I tried to install eclipse. I followed the how to at [http://sablevm.org/wiki/Debug](http://sablevm.org/wiki/Debug)
but i get this error

Eclipse from /usr/local/eclipse is starting up using /usr/local/bin/java-sablevm JVM.
Please be patient...
!SESSION Sep 19, 2005 14:43:27.408 ---------------------------------------------
eclipse.buildId=I200408122000
java.version=?
java.vendor=?
BootLoader constants: OS=linux, ARCH=ppc, WS=gtk, NL=en_US

!ENTRY org.eclipse.osgi Sep 19, 2005 14:43:27.430
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Native library `swt-pi-gtk-3101' not found (as file `libswt-pi-gtk-3101') in gnu.classpath.boot.library.path and java.library.path
   at java.lang.Runtime.loadLibrary (Runtime.java:778)

---

