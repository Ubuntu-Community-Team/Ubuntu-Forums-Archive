---
title: "sun-j2sdk1.5 dangling symlinks"
date: 2005-07-22
forum: Bug Reports / Support
---

### Post by sjmorgan on 2005-07-22
```
bainbridge:~% symlinks /etc/alternatives | grep dangling
dangling: /etc/alternatives/netscape-javaplugin.so -> /usr/lib/j2sdk1.5-sun/plugin/i386/ns4/libjavaplugin.so
dangling: /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
dangling: /etc/alternatives/firefox-javaplugin.so -> /usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```
EDIT: Also, they don't get removed when you --purge remove the package.

---

### Post by sjmorgan on 2005-07-22
Also, they don't get removed after you --purge remove the package.

---

