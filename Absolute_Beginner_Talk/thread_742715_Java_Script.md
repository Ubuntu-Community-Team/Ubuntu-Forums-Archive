---
title: "Java Script"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by lwalters6 on 2008-04-02
Trying to write wall posts and use scrabble application off Facebook and not able to. Homepage states i need to update my java script. Went to that website but it seems it is only for windows?? Please help

---

### Post by spiderbatdad on 2008-04-02
Assuming you have installed ubuntu-restricted-extras or java-6-sun

lets see...i fixed the issue for me with this site: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/173966](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/173966)

created the symbolic link: ```
$ sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so
$ cd /usr/lib/firefox-addons/plugins/
$ sudo ln -s /etc/alternatives/firefox-3.0-javaplugin.so
```

also installed: icedtea-gcjwebplugin_1.0-0ubuntu3

---

