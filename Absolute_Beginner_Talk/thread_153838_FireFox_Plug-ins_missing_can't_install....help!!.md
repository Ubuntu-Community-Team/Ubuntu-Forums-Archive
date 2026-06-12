---
title: "FireFox Plug-ins missing? can't install....help!!"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-04-01
Hi,

Would anyone know why I can't install flashplayer, Acrobat reader, or Jave runtime environment on my 64 bit breezy? I get the following errors:

admin@ubuntu:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
admin@ubuntu:~$
admin@ubuntu:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  acroread-debian-files
E: Package acroread has no installation candidate



This is weird? maybe wrong commands? ](*,)

---

### Post by JoshHendo on 2006-04-01
Try [automatix](http://ubuntuos.com/2006/02/automatix-easy-installation.html), that may work :)

---

### Post by gordong11 on 2006-04-01
I cant install it on on 64bit my usname -r is amd64_generic, and not i386.

Unless there is one for 64bit?

---

### Post by aysiu on 2006-04-01
These two links *may* help:
[https://wiki.ubuntu.com/RestrictedFormats#head-83aab3cae30dbbab8f1f695a8df72b4b01ab87a0](https://wiki.ubuntu.com/RestrictedFormats#head-83aab3cae30dbbab8f1f695a8df72b4b01ab87a0)
[https://wiki.ubuntu.com/RestrictedFormats#head-f4b5a0e592cf89fac0bb7f5388c8e1733413af21](https://wiki.ubuntu.com/RestrictedFormats#head-f4b5a0e592cf89fac0bb7f5388c8e1733413af21)

---

### Post by gordong11 on 2006-04-01
WOW Thanks!

I can understand Java on a 64-bit platform....but Acrobat reader? I guess it's a general plug-in thing for 64 bit architecture.

---

