---
title: "[SOLVED] Java MP3 Gain - trying to make it work"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-22
I have installed MP3Gain, and have downloaded the Java GUI (JavaMP3Gain_20040902_3.zip)

According to the instructions, I just need to do this:

```
steve@steve-desktop:~$ java -jar /home/steve/JavaMP3Gain/JavaMP3Gain.jar
```

but I get this back:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at JavaMP3Gain.<init>(JavaMP3Gain.java:19)
   at JavaMP3Gain.main(JavaMP3Gain.java:628)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more
```

What does that mean? What do I need to do?

Thanks in advance!

---

### Post by realvz on 2007-10-22
do u hv java runtime installed??
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by qprfact on 2007-10-22
That did it! Thanks!

---

### Post by realvz on 2007-10-22
Enjoy Ubuntu

---

