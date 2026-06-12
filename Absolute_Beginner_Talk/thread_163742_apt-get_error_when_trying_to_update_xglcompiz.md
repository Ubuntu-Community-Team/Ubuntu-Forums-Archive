---
title: "apt-get error when trying to update xgl/compiz"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-04-21
I get the following error when trying to do an apt-get update to get the latest version of xgl/compiz:
```
Get:1 http://www.beerorkid.com dapper/main xserver-xgl 7.0.0-0ubuntu5 [2313kB]
Fetched 2313kB in 3s (685kB/s)
(Reading database ... 86141 files and directories currently installed.)
Preparing to replace xserver-xgl 7.0.0-0ubuntu4 (using .../xserver-xgl_7.0.0-0ubuntu5_i386.deb) ...
Unpacking replacement xserver-xgl ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can't make heads or tails of it. What's the problem? ](*,)

---

### Post by GregoryD on 2006-04-22
Exact same error I get.

---

### Post by ruffneck on 2006-04-22
can anyone help with this? In my case I added both...

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

...to my /etc/sources.list

---

### Post by pbaehr on 2006-04-22
Good to see I'm not alone, I guess. Hopefully someone will come back with a brilliant solution.

---

### Post by -X- on 2006-04-23
> E: /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core

Eeeevil. But yeah, lets hope someone comes along... Soon...

---

### Post by Rui Pais on 2006-04-24
Hi,
you could do:
```
sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz
```
to avoid it.

It worked for me.

---

