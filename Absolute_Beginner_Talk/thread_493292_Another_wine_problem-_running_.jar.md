---
title: "Another wine problem- running .jar"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by SexyLexie on 2007-07-05
I'm trying to run a .jar program in ubuntu. When I try to run it through java, I receive the message "java.lang.NullPointerException
   java.io.File.<init>(File.java:222)
   com.desertphoenix.risen.RisenLauncher.<init>(RisenLauncher.java:38)
   com.desertphoenix.risen.RisenLauncher.main(RisenLauncher.java:199)"

When I try to run it with wine, nothing happens.

What can I do?

---

### Post by vexorian on 2007-07-05
are you using sun's Java?

IMHO, you shouldn't really expect that to work correctly with WINE, unless you install Java on WINE which sounds quite bizare.

All in one, this exception sounds as Java version incompatibility

---

