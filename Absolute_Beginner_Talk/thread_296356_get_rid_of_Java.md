---
title: "get rid of Java"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by in_orbit on 2006-11-09
I get the following error on execution of a piece of Java code: "Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit". As far as I understand this is due to the fact that the Java version which comes along with Ubuntu is kind of lousy. How do I get rid of this version and instead install Sun's Java?

/In orbit

---

### Post by taurus on 2006-11-09
Use Automatix and it will install and configure java for you...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by steve.horsley on 2006-11-09
Or alternatively, package sun-java5-jre is in the repositories.

---

### Post by zadax on 2006-11-12
you have to enable "multiverse" and "universe" options under "software properties". then install the "sun java" from the synaptic package manager. then run "update-alternatives --config java" from the command line and select sun's java.

---

