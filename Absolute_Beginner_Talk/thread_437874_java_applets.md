---
title: "java applets"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by deknakker on 2007-05-09
im having trouble running applets.
i installed al the java runtime plugins because that seemed to be suggested on the given site im trying to view.

still it says failed to load applet

in the java log it says:

[HTML]ava.lang.ClassNotFoundException: GesKraft.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:162)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:123)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:566)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:619)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1879)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:548)
	at sun.applet.AppletPanel.run(AppletPanel.java:299)
	at java.lang.Thread.run(Thread.java:534)
Caused by: java.io.IOException: open HTTP connection failed.
	at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:265)
	at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:43)
	at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:152)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:149)
	... 9 more
[/HTML]

im looking at applets on a dutch site so it may be a language problem?? 

i got 

Java 1.4 plugin for mozilla/firefox
 Java Web Start 1.4

 Sun Java 5.0 Plugin
 Sun Java 5.0 Runtime
 Sun Java 6 Web Start

all installed..

Using ubuntu feisty fawn, hope thats enough info, and thanks in advance, would greatly help for my school assignment

cheers 
John

---

### Post by LaRoza on 2007-05-09
When you installed the plugin, did you restart?

Do other applets work?

---

### Post by deknakker on 2007-05-09
ok i tried restarting didnt work

this is the site im trying to view: 

[http://www.haycap.nl/app-c/vector3D/vector3D.htm](http://www.haycap.nl/app-c/vector3D/vector3D.htm)

hmm good question do other applets work, 
not on this site..

*5 min surfing*

other applets do work

* 5 min asking roomy on windows computer*

ok, and the first applets that didnt work here didnt work on his computer 

thanks for the help, i guess that kinda solved it.. :D

Cheers!

---

### Post by LaRoza on 2007-05-09
There was no applet for me on that site either.

---

### Post by deknakker on 2007-05-09
yeah soz it was obviously a problem of that site..

me = noob

as in the words of .. in the hitchhikers guide to the galaxy

sorry for the inconvenience

---

### Post by LaRoza on 2007-05-09
"Share and Enjoy!"

---

