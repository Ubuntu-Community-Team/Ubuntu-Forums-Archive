---
title: "Exception when using Java app"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by jdfoote on 2008-04-20
When using the family search indexing (familysearchindexing.org) Java app, which works fine on Windows, I recently started getting an error on my Hardy Heron box.

The program opens fine, but whenever I attempt a certain operation, I get an error with the following stacktrace:

java.lang.SecurityException: sealing violation: can't seal package com.sun.media.jai.codec: already loaded
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:235)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
 
Any ideas about a way to fix it, or is it a bug in the app?

---

### Post by Diabolis on 2008-04-21
The exception is related to missing jar files or libraries.

I went to the site and downloaded the application, I couldn't run it at first.
Since it is a web application, it needed the correct plug in.
```
sudo apt-get install j2re1.4-mozilla-plugin
```

It seemed to run fine, I got another exception but it popped out because I don't have a user name.

---

### Post by jdfoote on 2008-04-22
I couldn't find the package, either through the command line or in synaptic. Could it have to do with the fact that I am running Hardy? Any other ideas?

The program loads just fine - I can log in, etc. When I click download batch, it downloads a batch, but then gives me the exception when it tries to open it.

---

### Post by Diabolis on 2008-04-22
Is hard to find a solution if I'm not able to run the application.
The problem could be with the path to the file you are trying to open, maybe the application is not finding it. Since its a web app, the file could be intended to be open directly from the site.

---

### Post by jdfoote on 2008-04-22
Thanks for trying, anyway. I tried to run it from the web, but I had the same problem.

---

### Post by Cymerej on 2008-05-07
I am having the same error.  The software was working with no problems under Gutsy, but now that I have upgraded to Hardy, I have no such luck.  I believe that I had Sun Java 5 and Sun Java 6 installed under Gutsy.  Under Hardy, I only have Sun Java 6.  I wonder if that might be the problem.

---

### Post by Cymerej on 2008-05-18
I tried installing the web app under java 1.5 and it wouldn't install.  I received an error indicating that the I was using the wrong JRE version (it was expecting 1.6+)

I tried installing with java 1.5 and java 1.6 both on the system.  If I used 1.5 for the installation, the install failed as before.  If I used 1.6, the app installed just fine, but would crash as before with the java exception error.  

I found this thread on the Sun Java.net forums 
[http://forums.java.net/jive/thread.jspa?messageID=273528]("http://forums.java.net/jive/thread.jspa?messageID=273528")

It is basically someone who had the same problem with another web app.  They attributed the error to a change from java 6 update 5 to java 6 update 6, which is the version Hardy is using.  He was able to fix the problem by recompiling the application with the new update.  Since I don't have access to the source code the  the application I am using, I don't have this option.

---

### Post by abruegl on 2008-06-03
Hi,

I was the one who posted the thread to the Java Forums that you referenced. This is actually a bug known by Sun:
[http://bugs.sun.com/view_bug.do?bug_id=6709297](http://bugs.sun.com/view_bug.do?bug_id=6709297)

There is also some more detail on that thread now about it, but I certainly would hope and expect soon. Here's a link back to that thread:
[http://forums.java.net/jive/thread.jspa?messageID=273528](http://forums.java.net/jive/thread.jspa?messageID=273528)

---

