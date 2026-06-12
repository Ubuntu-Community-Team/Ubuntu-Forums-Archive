---
title: "Java Problem"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-25
I'm trying to install Jose on my Ubuntu (6.10) installation. java -version reports: 
 
java version "1.4.2" 
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7) 
 
If I run java ~/jose/jose.jar from the command line, I get: 
 
Exception in thread "main" java.lang.NoClassDefFoundError: .home.willbur.jose.jose.jar 
at gnu.java.lang.MainThread.run(libgcj.so.70) 
Caused by: java.lang.ClassNotFoundException: .home.willbur.jose.jose.jar not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}} 
at java.net.URLClassLoader.findClass(libgcj.so.70) 
at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70) 
at java.lang.ClassLoader.loadClass(libgcj.so.70) 
at java.lang.ClassLoader.loadClass(libgcj.so.70) 
at gnu.java.lang.MainThread.run(libgcj.so.70) 
 
If I run java -jar jose.jar I get: 
 
Failed to load Main-Class manifest attribute from jose.jar 
 
I'm clearly a Linux newbie in need of some help!

---

### Post by deadgobby on 2007-01-25
Hi ya,
 Well let try this. Lets get all the goodies at once. Here is a link to Automatix and please read before you install. 
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Or Easy Ubuntu is cool too
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Automatix takes up to an hour to install. Depending on what you want to install. Easy Ubie takes little time.

Gobby

---

### Post by willbur on 2007-01-26
Thanks, gobby - I'll give it a try :D

---

### Post by pesach on 2007-01-26
Are you using mozilla firefox?
You might want to consider trying swiftfox which you can also find in automatix.

---

### Post by Ben Sprinkle on 2007-01-26
Just install Sun's...

---

