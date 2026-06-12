---
title: "jajuk with jre"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by OU812 on 2007-04-14
Hello. I needed to install jre for emusicj (a download manager for my music service). So I decided to install jajuk since it is a java app. I installed the .jar file rather than the .rpm file. According to their wiki, I should be able to launch it with "jajuk," but I get a not found error. I did find the installed folder, /usr/local/jajuk, but I only found two files that may be related to launching the app: .jar and .sh. Unfortunately, I don't know how to use either of them. The other option is to uninstall it and then install the .rpm file instead. But the uninstall file is .jar also. So right back to the beginning. Any help is appreciated.

john

---

### Post by OU812 on 2007-04-14
My bad. After awhile it sort of hit me: I somehow needed to launch it with java. So I did "man java" and problem solved

java -jar /path/to/filename.jar

and it worked.

john

---

### Post by 9000 on 2007-04-21
Trying the same install...

Exception in thread "main" java.lang.NoClassDefFoundError: jajuk-java-installer-1.3.7.jar
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: jajuk-java-installer-1.3.7.jar not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)


any thoughts?

---

### Post by Diabolis on 2007-10-19
9000, which steps you followed in order to install jajuk?

---

### Post by fsck222 on 2008-02-09
You can use the Jajuk Debian package on Ubuntu. You can download it on [http://jajuk.info/index.php/Download](http://jajuk.info/index.php/Download)

You need then to make sure you are using the correct Java version. Check [http://jajuk.info/index.php/Linux_Debian/Ubuntu/Kubuntu_installation_notes](http://jajuk.info/index.php/Linux_Debian/Ubuntu/Kubuntu_installation_notes)

--
fsck222 - [http://jajuk.info/](http://jajuk.info/)

---

