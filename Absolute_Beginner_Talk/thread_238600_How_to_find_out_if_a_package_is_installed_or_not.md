---
title: "How to find out if a package is installed or not?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by qsc on 2006-08-17
How to use apt-* to find if a specific package is installed or not, if installed, which version ? Many thanks!

---

### Post by h2gofast on 2006-08-17
aptitude show packageName
or just fire up synaptic and do a search for the package

---

### Post by scxtt on 2006-08-17
aptitude show <package name>

ex:```
[FONT="Courier New"]:> aptitude show vncserver
Package: vncserver
New: yes
[color=red]State: installed[/color]
Automatically installed: no
[color=red]Version: 3.3.7-8ubuntu2[/color]
Priority: optional
Section: universe/x11
Maintainer: Ola Lundqvist <opal@debian.org>
Uncompressed Size: 1270k
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.2), libice6, libsm6, libstdc++6 (>= 4.0.2-4), libx11-6, libxext6, zlib1g
         (>= 1:1.2.1), perl, xbase-clients, x11-common, vnc-common (>= 3.3.6-1)
PreDepends: dpkg (>= 1.6.8)
Recommends: xfonts-base
Suggests: vnc-java
Conflicts: vnc, vnc-doc
Replaces: vnc, vnc-doc
Provides: vnc-server, xserver
Description: Virtual network computing server software
 VNC stands for Virtual Network Computing. It is, in essence, a remote display system which allows you to view a
 computing `desktop' environment not only on the machine where it is running, but from anywhere on the Internet and from
 a wide variety of machine architectures.

 This package provides a server to which X clients can connect and the server generates a display that can be viewed
 with a vncviewer.

 Note1: This server does not support or need a display. You need a vncviewer to see something. However, this viewer may
 also be on a computer running other operating systems in the local net.

 Note2: A new version of vnc and is available in the vnc4server package. This package exist because of backward
 compatibility.[/FONT]
```looks like i just repeated what h2gofast said, oops ... ;)

---

### Post by qsc on 2006-08-17
Thanks for both of you. It's learned!

---

