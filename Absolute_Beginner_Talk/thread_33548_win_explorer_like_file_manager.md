---
title: "win explorer like file manager?"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-05-11
hello, im pretty new. my biggest problem in linux is that im struggling with the filesystem, not knowing where things are etc. it makes it worse that u ahve to click folders to navigate...is there a decent windows explorer style filemanager with a tree view on the left? that would make my migration a lot easier


thanks :_) ubuntu is really nice. i dont know what it is it just feels better than fedora which is the oher distro ive been messing with a bit

---

### Post by az on 2005-05-11
Nautilus can do that.  Just make this change:

[http://ubuntuguide.org/index.html#openeachfolderssamewindownautilus](http://ubuntuguide.org/index.html#openeachfolderssamewindownautilus)

---

### Post by glandula on 2005-05-11
thank you, i appreciate it. will try it out a little later

---

### Post by poofyhairguy on 2005-05-11
There is a better way. Just open up the regular terminal (not the root terminal) and enter this command!:

> gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true

---

