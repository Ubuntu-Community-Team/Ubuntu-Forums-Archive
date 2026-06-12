---
title: "i cant/t install latest version of monodevelop"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by simion314 on 2007-06-26
hi
I want  to instal monodevelop-0.14 . I found a .deb packege on getde website but it failed to install it sais that dependencies is not satisfiable libc6|libc6.1. I cant find this packeges in synaptic. If i use dpkg i get the folowing output:
simi@simi-laptop:~/app$ dpkg -i  monodevelop_0.14-1~getdeb1_all.deb
dpkg: requested operation requires superuser privilege
simi@simi-laptop:~/app$ sudo dpkg -i  monodevelop_0.14-1~getdeb1_all.deb
Selecting previously deselected package monodevelop.
(Reading database ... 105964 files and directories currently installed.)
Unpacking monodevelop (from monodevelop_0.14-1~getdeb1_all.deb) ...
dpkg: dependency problems prevent configuration of monodevelop:
 monodevelop depends on libc6 (>= 2.5-0ubuntu1) | libc6.1 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.
  Package libc6.1 is not installed.
 monodevelop depends on libgecko2.0-cil (>= 0.11-3); however:
  Package libgecko2.0-cil is not installed.
 monodevelop depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 monodevelop depends on libgtksourceview2.0-cil (>= 0.10); however:
  Package libgtksourceview2.0-cil is not installed.
 monodevelop depends on libgtksourceview2.0-cil (<< 0.11); however:
  Package libgtksourceview2.0-cil is not installed.
 monodevelop depends on libmono-cairo2.0-cil (>= 1.0); however:
  Package libmono-cairo2.0-cil is not installed.
 monodevelop depends on libmono-corlib2.0-cil (>= 1.2.3); however:
  Package libmono-corlib2.0-cil is not installed.
 monodevelop depends on libmono-sharpzip2.84-cil (>= 1.0); however:
  Package libmono-sharpzip2.84-cil is not installed.
 monodevelop depends on libmono-system-runtime2.0-cil (>= 1.0); however:
  Package libmono-system-runtime2.0-cil is not installed.
 monodevelop depends on libmono-system-web2.0-cil (>= 1.0); however:
  Package libmono-system-web2.0-cil is not installed.
 monodevelop depends on libmono-system2.0-cil (>= 1.2.3); however:
  Package libmono-system2.0-cil is not installed.
 monodevelop depends on libmono-winforms2.0-cil (>= 1.2.3); however:
  Package libmono-winforms2.0-cil is not installed.
 monodevelop depends on libmono1.0-cil (>= 1.2.3); however:
  Version of libmono1.0-cil on system is 1.1.17.1-1ubuntu7.
 monodevelop depends on libmono2.0-cil (>= 1.2.3); however:
  Package libmono2.0-cil is not installed.
dpkg: error processing monodevelop (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 monodevelop
simi@simi-laptop:~/app$ 

i have install mono using the installer from [http://www.mono-project.com/Downloads](http://www.mono-project.com/Downloads)
but it contains the verion .13 of monodevelop.  i have tried to compile it but i am not too good of this kind of installations.
Please help me to install this software(in synaptic is a very old ersion)

i belive that vhen i install mono using that installer it does/t place the libraies where the monodevelop expects to find them, ,neither ubuntu finds them.

---

### Post by Seisen on 2007-06-26
Which version of Ubuntu are you using?

---

### Post by simion314 on 2007-06-26
i have version 6.10

---

### Post by Seisen on 2007-06-26
That is the problem, the dependencies you need are in the feisty repositories.

---

### Post by simion314 on 2007-06-26
any solutions?

---

### Post by Seisen on 2007-06-26
You can upgrade to feisty or you can go through and download each individual package from here.

[http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by simion314 on 2007-06-26
can i upgrade my ubuntu without reinstalling? Thx for help

---

