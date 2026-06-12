---
title: "Java 6.0"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-03-03
I installed Java 5.0 from the Add/Remove thing, but theres this bug in it that I need to fix (where if you click outside of the applet you won't be able to type in that applet).

How do I upgrade to Java 6?

---

### Post by chewearn on 2007-03-03
Use Synaptic, search for sun-java.  You should see a tickmark next to java-sun5-jre and other java-sun5 related.  Uncheck jre (and all other java-sun5) to uninstall version 5.

Then, select java-sun6-jre and java-sun6-plugin.  java-sun6-bin should be selected automatically.  Click apply.

---

### Post by Baelfael on 2007-03-03
When I do it I only see sun-java5 ones. There aren't any 6 ones listed...

---

### Post by picpak on 2007-03-03
Do you have the backports repo enabled?

---

### Post by Baelfael on 2007-03-03
Ah, that did it. Thanks!

---

