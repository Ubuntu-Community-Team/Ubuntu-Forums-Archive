---
title: "Pidgin won't run in Kubuntu"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-06-27
title says it all.
i took the deb from here [http://www.ubuntugeek.com/install-pidgin-instant-messanger-in-ubuntu.html]("http://www.ubuntugeek.com/install-pidgin-instant-messanger-in-ubuntu.html")
and installed with "dpkg". But it won't run! :(

---

### Post by arochester on 2007-06-27
Download it from here and it does run in Kubuntu: [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

---

### Post by mendingo84 on 2007-06-27
been there. it gives some dependency errors!

---

### Post by mendingo84 on 2007-06-27
that's when downloading the deb packages. i'm trying with the archive now. hope it works

---

### Post by moredhel on 2007-06-27
make sure you install pidgin-data first.

EDIT: (it's next to the pidgin download.)

---

### Post by mendingo84 on 2007-06-27
yes...i did it that way. and when i type ```
sudo dpkg -i pidgin_2.0.2-1~getdeb1_i386.deb
```

it gives me 
```

(Reading database ... 91802 files and directories currently installed.)
Preparing to replace pidgin 1:2.0.2-1~getdeb1 (using pidgin_2.0.2-1~getdeb1_i386.deb) ...
Unpacking replacement pidgin ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libavahi-compat-howl0 (>= 0.6.0); however:
  Package libavahi-compat-howl0 is not installed.
 pidgin depends on libbonobo2-0 (>= 2.15.0); however:
  Package libbonobo2-0 is not installed.
 pidgin depends on libebook1.2-9 (>= 1.10.1); however:
  Package libebook1.2-9 is not installed.
 pidgin depends on libedata-book1.2-2 (>= 1.10.1); however:
  Package libedata-book1.2-2 is not installed.
 pidgin depends on libedataserver1.2-9 (>= 1.10.1); however:
  Package libedataserver1.2-9 is not installed.
 pidgin depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not installed.
 pidgin depends on libgtkspell0 (>= 2.0.2); however:
  Package libgtkspell0 is not installed.
 pidgin depends on libnm-glib0; however:
  Package libnm-glib0 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin

```

---

### Post by takakia on 2007-07-03
It works after you install all the dependencies....

---

### Post by ducksauce on 2008-03-18
You can fix all of the dependency errors in one shot just by doing "sudo apt-get -f install".

---

### Post by Oldsoldier2003 on 2008-03-18
unless you really want pidgin, kopete is better in KDE, and its a little better in its feature set.

---

