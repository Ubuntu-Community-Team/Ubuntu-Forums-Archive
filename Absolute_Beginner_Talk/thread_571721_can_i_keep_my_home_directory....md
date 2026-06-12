---
title: "can i keep my /home directory..."
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-09
with a reinstall of ubuntu?

---

### Post by Pumalite on 2007-10-09
Yes if it's in a separate partition. Just don't format it. If not, you can still backup /home, including 'Hidden Files' and later restore it.

---

### Post by w7kmc on 2007-10-09
You can keep it if you placed it on a separate partition.  Otherwise, it will get overwritten with a new install from CD.  It is possible to upgrade entirely using the update manager (via the net) and not lose /home.  Sometimes it can be buggy though, but my last upgrade from 6.10 to 7.04 went OK...here is the page I used for that one:  [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

If you are not sure if /home is mounted as its own partition, simply type df and if /home is not listed then it is not on a separate partition.  Usually, it is a good idea to place /home on a separate partition when you do an install so that it is not lost with full upgrades from a CD.  You just need to remember where its mounted and it should show up in the partition table, and remember not to format it ;)

---

