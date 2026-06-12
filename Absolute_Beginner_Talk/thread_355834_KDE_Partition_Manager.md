---
title: "KDE Partition Manager"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by opticyclic on 2007-02-07
Is there a KDE Partition Manager? 'KParted' maybe?
Or do you have to install GParted if you want a GUI?

---

### Post by jordanmthomas on 2007-02-07
QTparted

---

### Post by Sef on 2007-02-07
If you want to change the partitions on the os that is installed then get [GParted]("http://gparted.sourceforge.net").

---

### Post by AusIV4 on 2007-02-07
> **Sef said:**
> If you want to change the partitions on the os that is installed then get [GParted]("http://gparted.sourceforge.net").
GParted uses the GTK libraries, and thus is better suited for Gnome.
[QTParted]("http://qtparted.sourceforge.net/") uses the QT libraries, and thus is better suited for KDE. GParted will certainly work on KDE, but it will require loading GTK libraries that may have the same purpose as already loaded QT libraries.

Functionally, both are front ends for parted, so there shouldn't be a difference in their abilities to partition your hard drive.

---

