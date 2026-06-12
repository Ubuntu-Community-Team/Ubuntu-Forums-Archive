---
title: "Eclipse"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Korialstrasz on 2008-02-17
```
 JVM terminated. Exit code=1
/usr/lib/j2se/1.4/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 880043
-install /usr/lib/eclipse
-vm /usr/lib/j2se/1.4/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 
```


I have installed eclipse and the JVM and SDK, yet for some reason I get this error, I've seen it before on windows just forgot how to fix it, any help?

---

### Post by zanak on 2008-02-17
try to run eclipse trough terminal
# sudo eclipse -clean

---

