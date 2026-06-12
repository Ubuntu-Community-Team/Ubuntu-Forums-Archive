---
title: "Cdrom problem"
date: 2013-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pay3 on 2013-10-16
While upgrading it showed an error
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
can anyone tell what is the error how how reparir it.

---

### Post by slickymaster on 2013-10-16
The update manager is looking for packages on the Ubuntu CD/DVD. If it is not inserted you get that error. You can disable the CD as package source. Open the software center, go to Edit/Software Sources... and disable the CD on the first tab.

---

