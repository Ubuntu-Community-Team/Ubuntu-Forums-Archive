---
title: "Keyboard layout"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by voltage on 2007-02-26
Hi,

Do somebody can tell me how to change the  Keyboard layout using terminal window ? It is a server, there is no X installed... anyway below is what i done ...

1 ) $sudo apt-get install console-tools

2 ) $sudo dpkg-reconfigure console-data

error...

Package `console-data' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: console-data is not installed


Thx

---

### Post by bapoumba on 2007-02-26
Hi,
have you installed console-data (universe repositories) ?

---

### Post by voltage on 2007-02-26
> **bapoumba said:**
> Hi,
have you installed console-data (universe repositories) ?

I have try to locate the package by $sudo apt-get install console-data but its comes out the following message ...

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package console-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
However the following package replace it:
unicode-data
E: Package console-data has no installation candidate

After that I were try to install the unicode-data then I try to run $sudo dpkg-reconfigure console-data again. Then another message list below ...

Package `console-data' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: console-data is not installed

---

### Post by bapoumba on 2007-02-26
Can you post the output to **cat /etc/apt/sources.list**?

---

