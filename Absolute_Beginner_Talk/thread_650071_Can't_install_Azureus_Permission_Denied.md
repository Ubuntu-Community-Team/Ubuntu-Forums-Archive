---
title: "Can't install Azureus:: Permission Denied"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Casual_Mohammed on 2007-12-25
I dled a .jar file of Azureus but every time i try to install it Terminal keeps telling me permission denied.

> homer@Arbiter:~/Desktop$ ./Azureus3.0.4.2.jar
bash: ./Azureus3.0.4.2.jar: Permission denied
homer@Arbiter:~/Desktop$ 


---

### Post by taurus on 2007-12-25
Try this link.

[http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)

---

### Post by raycosm on 2007-12-25
Well it sounds like you just need to put 'sudo' before './Azureus3.0.4.2.jar'

```
sudo ./Azureus3.0.4.2.jar
```

---

### Post by articpenguin on 2007-12-25
try
> sudo ./Azureus3.0.4.2.jar

or getting azureus from getdeb.net

---

### Post by LaRoza on 2007-12-25
That is not how you run .jar files

```

java -jar app.jar

```

(I recommend a .deb)

---

### Post by Casual_Mohammed on 2007-12-25
> **LaRoza said:**
> That is not how you run .jar files

```

java -jar app.jar

```

(I recommend a .deb)

Tried that and this is what I got 

> homer@Arbiter:~/Desktop$ java -jar Azureus3.0.4.2.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.common.Main
   at java.lang.Class.initializeClass(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLineParser not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:Azureus3.0.4.2.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
homer@Arbiter:~/Desktop$ 

And I also tried the DEB and the package installer gave me an error saying wrong architecture

---

### Post by Steveway on 2007-12-25
Why not try a better and more lightweight torrent-client that also integrates better with the rest of your apps?
For example deluge?
Just install this and avoid the headaches Azureus gives you.

---

### Post by articpenguin on 2007-12-25
i think he wants vuze which is in azureus 3.

---

### Post by LaRoza on 2007-12-25
> **Casual_Mohammed said:**
> 
And I also tried the DEB and the package installer gave me an error saying wrong architecture

What Ubuntu do you use? And what processor?

---

