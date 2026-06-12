---
title: "Install LXDE on Modified Kernel"
date: 2011-09-16
forum: Any Other OS
---

### Post by rathin.saran on 2011-09-16
UPDATE:

I have installed CentOS 5.6.

I tried to install OpenBox and I am struck with the following :
when I did
./configure --prefix=/usr --sysconfdir=/etc
I got
Requested 'glib-2.0 >= 2.14.0' but version of GLib is 2.12.3

yum install glib2-devel
says that the package 2.12.3 is installed and there is nothing to update.

Please help.

---

### Post by rathin.saran on 2011-09-19
Finally, I have configured XFCE successfully.
I did the following:

    yum groupinstall "X Window System" "XFCE-4.4"

and everything was taken care of.

LINUX Rocks!!!

---

