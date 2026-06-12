---
title: "making a .bat work"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by darkenigma02 on 2008-02-01
How would I make a .bat file run under Ubuntu that has the code of
```

@title Sinscape Client

@java -cp ./SinScape.jar -Xmx500m client

@pause

```

---

### Post by darkenigma02 on 2008-02-01
Using 7.10 by the way.

Sorry for being so blatant with info... Let me know what you need if you need anything and how to get it (no good with coding or command lines)

---

### Post by conehead77 on 2008-02-01
Does the program start if you type this in the terminal:
```
java -cp ./SinScape.jar -Xmx500m client
```
?

---

### Post by darkenigma02 on 2008-02-01
I got
```
kyle@kyle-desktop:~$ java -cp ./SinScape.jar -Xmx500m client
Exception in thread "main" java.lang.NoClassDefFoundError: client
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: client not found in gnu.gcj.runtime.SystemClassLoader{urls=[], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)
kyle@kyle-desktop:~$ 

```

BTW can you link me to any good tutorial sites on help to learn coding/command lines?

---

### Post by conehead77 on 2008-02-01
Hm, sorry i cant help you here. Maybe you need to install some java thingies first (like jree or jdk) but im not sure about that.
Maybe you find something useful if you google the error messages.

As for command line help try this link:
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by Nythain on 2008-02-01
and a google search for "bash scripting" will give many tutorial sites on writing bash scripts... once you get the hang of it, you can do much easily :)

---

