---
title: "Java and Facebook"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-03-17
i have installed sun java 9 according to this post [http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox). and when i try to add photos to my face book the add spot goes blank with an red x in the top left corner when i right click the x and open the java counsel this is what it says.

load: class com.facebook.facebookphotouploader.FacebookPhotoUploader not found.
java.lang.ClassNotFoundException: com.facebook.facebookphotouploader.FacebookPhotoUploader
	at sun.applet.AppletClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.applet.AppletClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.applet.AppletClassLoader.loadCode(Unknown Source)
	at sun.applet.AppletPanel.createApplet(Unknown Source)
	at sun.plugin.AppletViewer.createApplet(Unknown Source)
	at sun.applet.AppletPanel.runLoader(Unknown Source)
	at sun.applet.AppletPanel.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
Caused by: java.io.IOException: open HTTP connection failed.
	at sun.applet.AppletClassLoader.getBytes(Unknown Source)
	at sun.applet.AppletClassLoader.access$100(Unknown Source)
	at sun.applet.AppletClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	... 10 more

any ideas?

---

### Post by dstew on 2007-03-17
In firefox, type about:plugins to see if you have the Java plugin installed correctly.

---

### Post by juniah on 2007-11-01
Im having a similar problem.  My applets aren't working either.  I've check my java plugins and they're all up to snuff.  Java and JavaScript are enabled in Firefox.  But when I try to use a Facebook applet, all I get is a grey box.  Any ideas?

---

