---
title: "Installing program"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by ianaaji on 2006-07-28
My first question is about .jar files, sort of. Basically, I want to install kolmafia [https://sourceforge.net/project/showfiles.php?group_id=126572](https://sourceforge.net/project/showfiles.php?group_id=126572)

And it comes in two different platform-independant downloads. I can't figure out the source package, or the .jar package. I'm fairly sure that I have all the java packages installed on my system. Can anyone help?

---

### Post by OU812 on 2006-07-28
Will this help?

[http://www.ubuntuforums.org/showthread.php?t=171822](http://www.ubuntuforums.org/showthread.php?t=171822)

john

---

### Post by ianaaji on 2006-07-29
Thank you for the link, but that didn't help. When I try that, it tells me that there is no config file, or a makefile. ./config and make commands don't do anything. When I untar the file, I get 2 directories and a file called build.xml which, as far as I knew, .xml is a webpage.

---

### Post by abowman on 2006-07-29
Try:
```

java -jar nameOfFile.jar

```
If that doesn't work you probably don't have java installed on your system.

---

### Post by ianaaji on 2006-07-29
I ran that command and this is what the terminal gave me:

Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.NullPointerException
   at javax.swing.JEditorPane.registerEditorKitForContentType(libgcj.so.7)
   at net.sourceforge.kolmafia.KoLmafia.<clinit>(Unknown Source)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...2 more

---

### Post by abowman on 2006-07-29
It looks like you have the default version of java that comes with Ubuntu.
I tried running that program and it runs fine for me, but I have Suns java on my computer.
This is how I installed java:
[http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/ ]("http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/")

---

### Post by ianaaji on 2006-07-29
Ok, I installed suns java following those instructions with no problems, then I tried to run java -jar javafile.jar (With the proper name of the file) and I got that same error again.

Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.NullPointerException
   at javax.swing.JEditorPane.registerEditorKitForContentType(libgcj.so.7)
   at net.sourceforge.kolmafia.KoLmafia.<clinit>(Unknown Source)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...2 more

---

### Post by abowman on 2006-07-29
It still looks like you have gnu java installed.
What do you get when you type:
```

java -version

```

---

### Post by ianaaji on 2006-07-29
I though I had removed the GNU java, but when I checked Synaptic it was still there, so I removed it and now it works, thank you :)

---

