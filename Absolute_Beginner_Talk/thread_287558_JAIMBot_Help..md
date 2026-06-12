---
title: "JAIMBot Help."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Recovered on 2006-10-28
I keep getting this error in Terminal after I try to run the bot. Can anyone help me? I'm pretty new to the deal. Thanks 
 
gabe@gabe-laptop:~/Desktop$ java -classpath "jaimbot-1.4:lib/rdf-1.0.jar:lib/megahal-1.0.jar:conf" com.levelonelabs.aimbot.AIMBot 
Exception in thread "main" java.lang.NoClassDefFoundError: com.levelonelabs.aimbot.AIMBot 
at gnu.java.lang.MainThread.run(libgcj.so.7) 
Caused by: java.lang.ClassNotFoundException: com.levelonelabs.aimbot.AIMBot not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jaimbot-1.4/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}} 
at java.net.URLClassLoader.findClass(libgcj.so.7) 
at java.lang.ClassLoader.loadClass(libgcj.so.7) 
at java.lang.ClassLoader.loadClass(libgcj.so.7) 
at java.lang.Class.forName(libgcj.so.7) 
at gnu.java.lang.MainThread.run(libgcj.so.7)

---

