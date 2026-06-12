---
title: "installing xnview"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-22
i have just downloaded xnview from

[http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html](http://perso.orange.fr/pierre.g/xnview/endownloadlinux.html)

i chose the "XnView v1.70 + NView/NConvert v4.51" tar version and extracted the files. now, how do i install it????

---

### Post by GeekSpeek'r on 2006-08-22
mkdir /usr/share/xnview
cp wherveritis to /usr/share/xnview/
cd /usr/share/xnview
tar xvf whateveritis
follow the README file or INSTALL file instructions

If it fails, repost here; you may have unmet dependencies or a gcc / make install issue

best of luck

---

### Post by k94382 on 2006-08-22
just found this

[http://www.ubuntuforums.org/showthread.php?t=73651&highlight=xnview](http://www.ubuntuforums.org/showthread.php?t=73651&highlight=xnview)

so what are the differences and advantages between tar and RPM????

---

### Post by TFX360 on 2006-08-22
k94382,

Rather between rpm and deb. *.deb are packages for Debian and since ubuntu is based on Debian... go figure. The alien command in that thread was new to me.


Kind regards,


TFX

---

### Post by Jagot on 2006-08-22
> **k94382 said:**
> so what are the differences and advantages between tar and RPM????

A tar contains source code which requires you to compile it.  An rpm is a binary file which has already been compiled.

---

### Post by k94382 on 2006-08-22
yea i know by now that for deb files u just double click like in windows and then install. so all tar files are compressed sources?? RPMs usually work with ubuntu then?

---

