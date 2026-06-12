---
title: "Update Manager killed Azureus!"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-08-24
I left my computer on overnight downloading bittorrents, wake up to find Azureus has shut down and Update Manger is there instead.  The little frog is gone from the notification area and replaced with the yellow star!

Is this a bug (seems quite an important one) or something else? How do I stop it happening?

---

### Post by swoll1980 on 2007-08-24
were your downloads complete?

---

### Post by Spike-X on 2007-08-24
That's odd. Perhaps it's just a coincidence? ie Azureus crashed, and Update Manager just happened to pop up?

---

### Post by aberadam on 2007-08-24
I tried to restart Azureus, it showed it loading then it flicked up momentarily and disappeared.  Just tried rebooting and the same.  I can't get into Azureus.  

When I left it last night it was running fine.

---

### Post by aberadam on 2007-08-24
Could be Spike-X, I don't know.

---

### Post by aberadam on 2007-08-24
I've tried to start Azureus 5 times, nothing showing in System Monitor. 

Weird.

---

### Post by aberadam on 2007-08-24
I tried removing and reinstalling with Add/Remove, same problem of loading up then disappearing...

---

### Post by aberadam on 2007-08-24
I just completely purged Azureus, reinstalled from Add/Remove and it still disappears a split second after loading up.

---

### Post by shinjimx on 2007-08-24
Got the same problem, it also refused to load after some updates i downloaded today, any ideas?

---

### Post by wormser on 2007-08-25
This [post]("http://ubuntuforums.org/showpost.php?p=1680674&postcount=13") resolved my issues.  

> Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

This is only going to work if the repositories have not updated to the latest Azureus2.jar.  It seems to resolve most Azureus bugs.

---

### Post by Doodles2000 on 2008-01-19
Same problem here to, let update manager do the updates, re-boot, try to load up azureus (from the terminal) and the following error appears:

mark@mark-ubuntu:~$ azureus
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/widgets/Display (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
mark@mark-ubuntu:~$ 


Have tried complete remove and re-install via synaptic manager, also tried re-installing java, the same error appears..... maybe I am missing something ?
any help/ideas would be appreciated

---

