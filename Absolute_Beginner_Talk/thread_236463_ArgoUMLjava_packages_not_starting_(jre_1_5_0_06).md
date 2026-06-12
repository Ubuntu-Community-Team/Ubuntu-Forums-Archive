---
title: "ArgoUML/java packages not starting (jre_1_5_0_06)"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by neocookie on 2006-08-14
Hi guys

I'm having a nightmare with this one. I can't seem to get java working for me at all.

I'm trying to use two programs: ArgoUML and FDDManager. Both are java apps. Neither will start under Dapper using jre_1_5_0_06 either installed through synaptic or manually.

The install for ArgoUML is a simple unzip process, however FDDManager uses a java installer, which executes as expected. After that, it just won't run. I've got the same things running fine on my windows machines both at work and at home, but can't seem to get them up and running on my Dapper-lappy.

And ideas why they might not be starting?

---

### Post by meng on 2006-08-14
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
Selecting default java (Sun as opposed to others)
If this is not the problem, you should probably specify what error messages you are getting.

---

### Post by chonger on 2006-08-14
What is the command you are using to start ArgoUML?

Are you (on Unix) following the instructions on this [page]("http://argouml.tigris.org/")?

3b. On Unix: Type the command 'java -jar argouml.jar'

What's the Exception/stack trace you are seeing. Also, to get an idea of your level with Java, how familiar are you with debugging a Java process that fails to start?

---

### Post by neocookie on 2006-08-14
chonger: thats the command i'm typing. i don't actually get an error message. the cpu runs hot for a short while, then slows down, then nothing.

as for debugging - i'm not a java developer at all. php/perl/ruby, yes, but i normally run away from java. ;)

---

### Post by chonger on 2006-08-15
> **neocookie said:**
> chonger: thats the command i'm typing. i don't actually get an error message. the cpu runs hot for a short while, then slows down, then nothing.

as for debugging - i'm not a java developer at all. php/perl/ruby, yes, but i normally run away from java. ;)

Cool. That's a good start. You can probably see the java process using the ps command (something like > ps -aefwwww | grep java). Is the process running? If so, it looks like Java started the application was unable to draw to the screen. Or maybe it started up but is hiding somewhere on the desktop(?).

Can you run any other Java-based applications? For example, a simple Java application like beanshell ([www.beanshell.org)](www.beanshell.org)).

Also, you can start the app by calling its Main class directly, using something like:

> 
java -classpath argouml.jar org.argouml.application.Main


Also, I am assuming you have some kind of Desktop (KDE/Gnome/Xfce) installed.

---

### Post by chonger on 2006-08-15
One other thing. It looks like ArgoUml creates a log file named "argouml.log". Let's see if you can find any errors in there.

---

### Post by neocookie on 2006-08-16
Thanks chonger. I'll give your suggestions a try tonight. :)

---

### Post by neocookie on 2006-08-21
OK, so I tried to get FDDManager running, and using this command:```
java -Xmx512m -Djava.library.path="/usr/local/FDDManager/lib" -jar "/usr/local/FDDManager/FDDManager.jar" %1
``` I got the following error: ```
Exception in thread "main" java.lang.ClassNotFoundException: sun.misc.BASE64Decoder not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/local/FDDManager/FDDManager.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at nz.co.tracit.security.Util.decodeBase64(Util.java:267)
   at nz.co.tracit.security.license.impl.SimpleLicenseImpl.isValid(SimpleLicenseImpl.java:220)
   at nz.co.tracit.fdd.ui.FDDManager.showConsoleBanner(Unknown Source)
   at nz.co.tracit.fdd.ui.FDDManager.main(Unknown Source)
```

I've no idea why its throwing a BASE64Decoder error... thought that was standard with the jvm... Any ideas what it might be?

---

### Post by neocookie on 2006-08-21
Cracked it. Can't believe I was so daft. Getting too used to the ease of Ubuntu, I think.

Didn't set the java paths in my .bashrc file. :rolleyes:

---

### Post by dbusse on 2007-10-19
I have a similar problem.  I have sun java 1.5.0.11 installed.  However ArgoUML will not run correctly.  The program will display the splash screen and then show a window.  There there are no controls painted in the window.  I have another program that uses the JRE called FreeMind which runs with no problem.
Any suggestions would be welcomed.

---

