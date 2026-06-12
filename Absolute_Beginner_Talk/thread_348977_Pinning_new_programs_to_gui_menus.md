---
title: "Pinning new programs to gui menus"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by broncbuster on 2007-01-29
Hey y'all.  Is there a way to pin a shortcut to a newly installed program to a menu or the desktop when you install it from an .rpm?  I'm trying to install VNC and I can't figure this out.  It's not running right.

Here's what i did and the responses i got from terminal.

administrator@LinuxBox:~/Desktop$ sudo alien -i vnc.rpm
Warning: Skipping conversion of scripts in package vnc: postinst
Warning: Use the --scripts parameter to include the scripts.
dpkg: regarding vnc_4.1.2-2_i386.deb containing vnc:
 xvncviewer conflicts with vnc
  vnc (version 4.1.2-2) is to be installed.
dpkg: error processing vnc_4.1.2-2_i386.deb (--install):
 conflicting packages - not installing vnc
Errors were encountered while processing:
 vnc_4.1.2-2_i386.deb
administrator@LinuxBox:~/Desktop$

---

### Post by someusernoob on 2007-01-29
Im sure there is both a VNC server and a client in the Ubuntu repositories. They are also installed by default (on Edgy).

That is also what the error you get says. The package you try to install conflicts with the xvncviewer package.

So first explain why you want to install the VNC rpm before trying to solve this "problem".

---

### Post by broncbuster on 2007-01-29
I don't know what the problem is.  I'm too linux illiterate to know what this means.  What do i need to do to fix the problem?

---

### Post by someusernoob on 2007-01-30
Well, the problem is that you want to install something that is actually already installed.

From your terminal output:"xvncviewer conflicts with vnc"

xvncviewer is also a vnc client. So I don't get why you want to install the VNC.rpm.

You could possibly uninstall xvncviewer and install the VNC.rpm anyway, but it doesn't make much sense to me.

---

