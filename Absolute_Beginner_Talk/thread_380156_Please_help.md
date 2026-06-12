---
title: "Please help"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by progrockusa on 2007-03-09
i'm trying to finish updating some nvidia drivers and when i use the command sudo apt-get install nvidia-glx it goes to download these two updates but it's going slower than 1 kbps says it'll take 15 hours. does anyone know where i can get these updates from somewhere else?


linux-restricted-modules-2.6-17-10-generic
linux-restricted-modules-2.6-17-11-generic

---

### Post by mikewhatever on 2007-03-09
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all)

---

### Post by Kateikyoushi on 2007-03-09
The server used for upgrading can be changed in System > Administration > Software sources.
Can be done manually as well by editing the /etc/apt/sources.list and adding a local mirror initials before the main server address.

For example I change this

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

To this

[http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/)

The local server can be more than ten times faster than the main for me.

---

### Post by progrockusa on 2007-03-09
where would be a good place to get these two updates

---

### Post by Kateikyoushi on 2007-03-09
In north america probably us or ca.

---

