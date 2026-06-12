---
title: "Trouble Installing JEdit"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Straevaras on 2006-10-06
Hello, not used to Linux much and trying to get used to it.  I'm currently trying to install JEdit and when I try I get the following:

```
straevaras@straevaras-laptop:~/Desktop$ java -jar jedit42install.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.JFrame.<init>(libgcj.so.7)
   at installer.SwingInstall.<init>(SwingInstall.java:30)
   at installer.Install.main(Install.java:35)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...6 more
straevaras@straevaras-laptop:~/Desktop$
```

I've tried extracting the jar file but there's nothing in there that helps me, and plus the installation notes on JEdit's website say that you run the Java Application Launcher.

Anyone happen to know what I'm doing wrong?

---

### Post by Ben Sprinkle on 2006-10-06
Download the latest JRE from: [http://Java.sun.com](http://Java.sun.com)
See if it does same thing, or try it without -jar.

---

### Post by NoWhereMan on 2006-10-06
you are using gcj (gnu compiler for java); install sun's jre 
[https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956](https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956)

bye :)

---

### Post by Straevaras on 2006-10-06
Sorry, but another newbie moment.  I download the rpm for the JRE in a bin file format.  How do I use this?

---

### Post by Ben Sprinkle on 2006-10-06
Do not get the rpm, get self extracting.
To run it:
```

./jre.bin

```

---

### Post by Straevaras on 2006-10-06
I'm still getting the same error after installing the latest JRE. 

And the same errors (as above in the first post) still happen with the -jar option.

What I used to install JRE
```
chmod 744 jre-1_5_0_09-linux-i586.bin
./jre-1_5_0_09-linux-i586.bin
```

---

### Post by NoWhereMan on 2006-10-06
that way it won't still add the created $PATH_TO_JAVA/bin to your $PATH; I still suggesto to install jre from synaptic. you'll have to enable universe repository; see the link i gave you ;)

---

### Post by Straevaras on 2006-10-06
I know this probably isn't a Ubuntu specific issue, but would anyone happen to know why I'm getting this message when I try to run JEdit?
```
straevaras@straevaras-laptop:~$ bin/jedit
GC Warning: Out of Memory!  Returning NIL!
Exception in thread "main" GC Warning: Out of Memory!  Returning NIL!
java.lang.NoClassDefFoundError: org.gjt.sp.jedit.jEdit
*** Got java.lang.OutOfMemoryError while trying to print stack trace.
straevaras@straevaras-laptop:~$
```

I really want to doubt that it's a RAM issue, because I have to 2GB of RAM.

---

### Post by Iandefor on 2006-10-17
There's a small constellation of packages in the repositories of official Java stuff. Enable Universe and Multiverse and try the following:```

sudo aptitude install sun-java5-bin sun-java5-plugin
``` I believe that may simplify the process of getting Java set up.

---

### Post by rcmullins on 2007-06-20
This thing is a bit of a pain, how do you fire it up?

---

### Post by rcmullins on 2007-06-20
Ok, this was dumb.

Navigated to /jedit/4.2  then ran java -jar jedit.jar

Which is NOT how they tell you to fire it up when installing.

---

### Post by rcmullins on 2007-06-20
OK, 5 minutes later, this is the ugliest thing I have just about ever seen in my life.  I'm going back to Quanta+

---

