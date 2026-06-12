---
title: "repository problem"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-19
When I was trying to do software updates, I get the following message when I click Reload.  How can I fix this?

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found

---

### Post by Ampersand on 2005-10-19
The mirrormax backports have been taken down. They still seem to be available at [http://archive.ubuntu.com/](http://archive.ubuntu.com/).

---

### Post by racermike1967 on 2005-10-19
so what do i do?  Is there anything special i need?

---

### Post by Ampersand on 2005-10-19
If you're using Ubuntu Hoary (version 5.04), run
```
sudo gedit /etc/apt/sources.list
```
and replace [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) with [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) (keeping the rest of the line the same).

If you've upgraded to Breezy the backports are redundant, so you can comment out  (by putting # at the start) or remove those lines.

---

### Post by jacobo on 2005-10-19
how are they redundant? 

i thought the point of backports was that didn't/wouldn't exist in the standard ubuntu rep's.

are the backports all in the regular repos now?

---

### Post by Ampersand on 2005-10-19
The backports allow you to use the applications from the developement release while you're still using the stable release, so if you're using Hoary you'll get packages from Breezy. You'll have to wait for Dapper to get close to stable before getting any Breezy backports. More information about it here: [https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

---

