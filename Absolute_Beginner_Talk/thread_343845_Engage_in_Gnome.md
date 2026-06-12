---
title: "Engage in Gnome"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-22
I was just wondering if engage works with gnome, or can it only be run with enlightenment.

I get this when i try to run it:

```
engage: error while loading shared libraries: libewl.so.0: cannot open shared object file: No such file or directory

```

Any Ideas?

---

### Post by ajmorris on 2007-01-22
don't worry i solved my problem. I used alien to convert an mandriva rpm to deb. The lib file is a mandriva requirement. I have found the site with the ubuntu repositories and have sucessifully installed and run engage.

---

### Post by ajmorris on 2007-01-22
ummm.... actually it doesn't work

i get this:

 File: /usr/lib/enlightenment/modules/engage/icons/xapp.eap is not up to date for key "collections/0" - needs rebuilding sometime
engage: icon.c:322: od_icon_arrow_show: Assertion `icon->icon' failed.
Aborted (core dumped)

---

### Post by Currahee on 2007-01-22
I successfully installed Engage on Gnome following this howto: [http://dnnd.netsons.org/archives/2006/12/01/engage-on-ubuntu-edgy-dapper/](http://dnnd.netsons.org/archives/2006/12/01/engage-on-ubuntu-edgy-dapper/)

---

