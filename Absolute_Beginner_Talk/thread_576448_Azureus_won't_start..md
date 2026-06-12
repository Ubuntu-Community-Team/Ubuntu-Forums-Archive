---
title: "Azureus won't start."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-10-15
ok, getting this error msg when I try to start it from a root:

```

changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/SWT (Unsupported major.minor version 49.0)
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
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:62)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:102)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)

```

Help plz...

cheerio

**EDIT:** I tried replacing the Azureus2.jar file. Didn't work.

---

### Post by moffa on 2007-10-15
Have you installed sun-java6-jre (or sun-java5-jre)?  If so, try downloading Azureus from it's website: [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

Cheers,

---

### Post by aktiwers on 2007-10-15
I would guess that you still need to install some java?

Else you could have a look at Deluge. Im a long time Azureus user too, but Deluge made me change. Its soo nice :)

[http://www.getdeb.net/app.php?name=deluge](http://www.getdeb.net/app.php?name=deluge)

---

### Post by Fixel on 2007-10-15
Ok, managed to fix it. 

I had installed the old java's (v5) and those conflicted with gutsy. 

(doc still didn't install... so I just removed it.)

Thx for you help.

---

