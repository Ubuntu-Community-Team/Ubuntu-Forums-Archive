---
title: "Eclipse and Java in 7.04"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by NS2-10 on 2007-06-27
Hey!

First of all, I am a noob so keep it simple people.

I recently installed Eclipse on my completly new Ubuntu system. From recommendations in various forums I installed sun-6-java for JAVA support using apt-get. I also installed a few other packages that I cant remember, because they where associated with JAVA (all in accordance with forum posts). To check that this was done correctly I ran:

Code:

dlang@dlang-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

Which is what I have been told I should get.

**BUT**, when I try to debug and compile a simple HelloWorld.java file in Eclipse I get the following error:

Code:

Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/dlang/workspace/AppletTester/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

Some one replied that it might be associated with CLASSPATH but that tells me nothing. Please explain more. Some one else replied that the "instaled JRE might point to the wrong package". Where do I check that and where should it point?

I am guessing that this is associated to some package that is either not there or in the wrong place.

Please help me get JAVA up and running. I need to program!

---

### Post by Pragmatist on 2007-06-27
What happens if you try to run the program in a terminal?  Try this:

```
javac HelloWorld.java
```

And then, 
```
java HelloWorld
```

Does this work?  Also, please post the output of this command:
```
echo $PATH
```

---

### Post by Inxsible on 2007-06-27
1) Open up Eclipse. 
2) Right Click the Java project and select Properties. 
3) Select Java Build Path on the left navigation menu
4) Under the Libraries tab, look for JRE System Library. Is it pointing to the correct Java installation on your system ?
 
If not, you will need to correct it. If the JRE is not present altogether, then you need to add it.

---

### Post by NS2-10 on 2007-06-27
First Pragmatist, eventhough I suspect something is wrong with what I did here, this is the output. I sense that there is something that I should have done differently.

dlang@dlang-laptop:~$ javac HelloWorld.java
javac: file not found: HelloWorld.java
Usage: javac <options> <source files>
use -help for a list of possible options

dlang@dlang-laptop:~$ java HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld

dlang@dlang-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

For Inxsible:

My JRE is pointing to *java-1.4.3-gcj-4.1-1.4.2.0*. This is not the JRE I intended to use, since I downloaded Sun 6 Java. When I try to find the JRE from Sun 6 I found some stuff with those names in /usr/lib/jvm/ although all those files are grayed out. How do I go about changing this to the correct JRE.

I don't understand much of this so please keep it really simple. All I want to do is practice making applets and simple code experiments.

---

### Post by Inxsible on 2007-06-27
> **NS2-10 said:**
> First Pragmatist, eventhough I suspect something is wrong with what I did here, this is the output. I sense that there is something that I should have done differently.
 
dlang@dlang-laptop:~$ javac HelloWorld.java
javac: file not found: HelloWorld.java
Usage: javac <options> <source files>
use -help for a list of possible options
 
dlang@dlang-laptop:~$ java HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
 
dlang@dlang-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 
For Inxsible:
 
My JRE is pointing to *java-1.4.3-gcj-4.1-1.4.2.0*. This is not the JRE I intended to use, since I downloaded Sun 6 Java. When I try to find the JRE from Sun 6 I found some stuff with those names in /usr/lib/jvm/ although all those files are grayed out. How do I go about changing this to the correct JRE.
 
I don't understand much of this so please keep it really simple. All I want to do is practice making applets and simple code experiments.
 
You are trying javac HelloWorld from your home folder? Is that where your file is?
file not found usually means you are in the wrong folder or you are using the wrong name or case. You probably know that HelloWorld.java is not the same as Helloworld.java

---

### Post by Pragmatist on 2007-06-27
Ok, let's find where the Java 1.6 files are located:

```
sudo updatedb
```wait until this finishes (it takes a few minutes)

Then, 
```
locate javac
```Your looking for something like this:  /usr/local/jdk1.5.0_10/bin/javac
If you installed java in /usr/local then it will be nearly the same except the jdk directory name will be different since your using a different version of java than I am.  If you find other versions of javac, don't worry about it for now.  We will just use the path for Java 1.6.0

Once you find the location, you need to update your path (again, you need to put your path here, not mine :) ):
```
PATH=$PATH:/usr/local/jdk1.5.0_10/bin
```

Notice that I'm only including the path up to the bin directory.  This will allow you to just type in the name of various commands such as javac and java without including the entire path each time.

Now try my previous experiment with javac and java.  If this works, at least you know the Java is working.  Next, now that you have the actual paths, you should follow inxsible's suggestion for configuring Eclipse.

---

### Post by tarek on 2007-06-27
Hi,

I had the same problem, Eclipse was using the open source java compiler. To fix that follow this tutorial, easy to fix:
For Java 5:
[http://blog.csmonkey.com/2007/06/how-to-make-sun-java-5-default-java.html]("http://blog.csmonkey.com/2007/06/how-to-make-sun-java-5-default-java.html")

For Java 6:
[http://ubuntuforums.org/showthread.php?t=201378]("http://ubuntuforums.org/showthread.php?t=201378")

---

