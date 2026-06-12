---
title: "phex"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-06-19
does anyone here know how to install phex on ubuntu? if not does anyone know a file sharing program on the (gnutella?) network that i can install?

---

### Post by avik on 2007-06-19
Try gtk-gnutella or frostwire.

---

### Post by chaumurky on 2008-03-17
[FONT=Arial]* DL the zip
* make a directory (as root) called /opt/phex
* extract (as root) contents of the 'Lib' folder in the zip file to /opt/phex
* create a text file (as root) called /usr/bin/phex and add the following:

#!/bin/sh
java -jar /opt/phex/phex.jar

* make it executable
* if you like make a launcher pointing to /usr/bin/phex
[/FONT]

---

### Post by vishzilla on 2008-03-17
gtk-gnutella
Its in the repos

---

