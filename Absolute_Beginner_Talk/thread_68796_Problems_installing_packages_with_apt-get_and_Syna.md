---
title: "Problems installing packages with apt-get and Synaptic"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by vordrax on 2005-09-24
Hello, I am following this guide to get Cadega running from CVS:
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

When I try to install the packages they ask me to, I get several errors:

```
********@ubuntu:~$ sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
Reading package lists... Done
Building dependency tree... Done
cvs is already the newest version.
bison is already the newest version.
libpng12-dev is already the newest version.
libjpeg62-dev is already the newest version.
libfreetype6-dev is already the newest version.
libxrender-dev is already the newest version.
libttf2 is already the newest version.
libfontconfig1-dev is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flex-old: Conflicts: flex but 2.5.31-31 is to be installed
  libasound2-dev: Depends: libasound2 (= 1.0.8-1) but 1.0.9-2 is to be installed
  libsdl1.2-dev: Depends: libsdl1.2debian (= 1.2.7+1.2.8cvs20041007-3ubuntu4) but 1.2.7+1.2.8cvs20041007-5.3ubuntu2 is to be installed
  msttcorefonts: Depends: cabextract (>= 0.1-2) but it is not going to be installed
  x-window-system-dev: Depends: libdps-dev but it is not going to be installed
                       Depends: libdps1-dbg but it is not going to be installed
                       Depends: libice6-dbg but it is not going to be installed
                       Depends: libsm6-dbg but it is not going to be installed
                       Depends: libx11-6-dbg but it is not going to be installed
                       Depends: libxaw7-dbg but it is not going to be installed
                       Depends: libxaw7-dev but it is not going to be installed
                       Depends: libxext6-dbg but it is not going to be installed
                       Depends: libxi6-dbg but it is not going to be installed
                       Depends: libxmu6-dbg but it is not going to be installed
                       Depends: libxmuu1-dbg but it is not going to be installed
                       Depends: libxp-dev but it is not going to be installed
                       Depends: libxp6-dbg but it is not going to be installed
                       Depends: libxpm4-dbg but it is not going to be installed
                       Depends: libxrandr2-dbg but it is not going to be installed
                       Depends: libxt6-dbg but it is not going to be installed
                       Depends: libxtrap6-dbg but it is not going to be installed
                       Depends: libxtst6-dbg but it is not going to be installed
                       Depends: libxv1-dbg but it is not going to be installed
                       Depends: pm-dev but it is not going to be installed
                       Depends: xlibmesa-gl-dev but it is not going to be installed
                       Depends: xlibmesa-glu-dev but it is not going to be installed
                       Depends: xlibmesa-gl-dbg but it is not going to be installed
                       Depends: xlibmesa-glu-dbg but it is not going to be installed
                       Depends: xlibosmesa4-dbg but it is not going to be installed
                       Depends: xlibosmesa-dev
                       Depends: xlibs-static-pic but it is not going to be installed
                       Depends: xspecs but it is not going to be installed
  xorg-driver-fglrx-dev: Depends: xorg-driver-fglrx (= 6.8.0-8.8.25-0ubuntu11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Ignore what is below this, I don't know why I tried to install the ATI drivers...

I tried the 'apt-get -f install' and got this:

```
********@ubuntu:~$ sudo apt-get -f install Reading package lists... Done Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B/3185kB of archives.
After unpacking 10.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 109617 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions? I'm using Breezy if that's what is causing it.

---

### Post by MetalHannes on 2005-09-24
What came on Synaptic?

---

### Post by vordrax on 2005-09-24
[QUOTE=MetalHannes]What came on Synaptic?[/QUOTE]

[[IMG]http://img128.imageshack.us/img128/2874/bug9yf.th.jpg[/IMG]](http://img128.imageshack.us/my.php?image=bug9yf.jpg)

[[IMG]http://img128.imageshack.us/img128/4128/bug23xg.th.jpg[/IMG]](http://img128.imageshack.us/my.php?image=bug23xg.jpg)

---

### Post by MetalHannes on 2005-09-24
Boy, I wish i could help you but somehow i think i have seen these problem (wel similar to them) on my pc :-k  :-k

---

### Post by vordrax on 2005-09-24
It seems like it's mad at me for having NEWER versions of these libraries.

---

### Post by vordrax on 2005-09-24
This is irritating. It wants me to delete my newer libraries and install older ones. Does anyone know a way around this?

---

### Post by vordrax on 2005-09-24
Bump, anyone?

---

### Post by vordrax on 2005-09-24
Bump, am I on the proper board?

---

