---
title: "java problems"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by lordharsha on 2006-06-12
I'm having problems getting java to work on my system. The program I'm trying to compile and run is a pretty simple one:

> class Sample{
	public static void main(String args[]){
		System.out.println("Hello World");
	}
}

I managed to compile it without any problems, but when I try running it, I get these errors:

> archangel@vault:~$ java Sample
Exception in thread "main" java.lang.UnsupportedClassVersionError: Sample (Unsupported major.minor version 49.0)
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

I doubt there's anything wrong with the program, so whats the problem due to?

---

### Post by JanVH on 2006-06-12
I think it's because you compiled it with Java 5 and are trying to run with a previous Java-version.

What do java -version and javac -version say? (the top line)

---

### Post by lordharsha on 2006-06-12
Hmm, that seems to be the problem. My version of java is
> java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

and javac is:
> javac 1.5.0_06

What i dont understand now is why I dont have java version 1.5.0. I'm pretty sure I've downloaded all the necessary packages thru synaptic.

---

### Post by Drakkor on 2006-06-13
I was able to install java,macromedia flashplayer,and a shitload of other programs
with Automatix

---

### Post by FyreBrand on 2006-06-13
[QUOTE=lordharsha]What i dont understand now is why I dont have java version 1.5.0. I'm pretty sure I've downloaded all the necessary packages thru synaptic.[/QUOTE]Check synaptic again to make sure.  It seems the JDK and the JRE are separate downloads.  Under the System -> Preferences menu there should be a menu item called "Sun Java 5.0 plug-in control panel".  If it's not there I would guess that the 5.0 JRE probably isn't installed.

Also if you're using eclipse to write and run your Java code then you need to make sure that the JRE it's using is 5.0.  You can tell it to compile to the 5.0 standard if you have it installed but you also need to tell it to run the 5.0 JVM.

I hope that helps some.

---

### Post by jvictor on 2006-06-13
1.4.2 which comes with Ubuntu which is Blackdown Java , not sun java 

The problem u r facing is due to differences in the serialVersion of the compiled classes

setSerialVersionUID() will also help, but the easier solution is to have the same version of compiler and java

---

### Post by JanVH on 2006-06-13
If you install Java 5 (what you probably did already):

```
sudo apt-get install sun-java5-jdk
```

you can select the right jre by doing:

```
sudo update-alternatives --config java
```

---

### Post by lordharsha on 2006-06-13
I got this done, am using blackdown for both now

---

### Post by JeremyWorst on 2006-06-21
PMFJI but I'm having the same problem.  Eclipse works ok but I can't do anything from the terminal.  javac and javadoc aren't found.  I tried
sudo apt-get install sun-java5-jdk
but I get the following:
jeremy@ubuntu:~$ sudo apt-get install sun-java5-jdk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jdk
jeremy@ubuntu:

I guess I'm missing something...?

---

### Post by incubus on 2006-06-22
Do you have multiverse activated in your repositories?

[http://www.ubuntuforums.org/showthread.php?t=198107&highlight=jdk](http://www.ubuntuforums.org/showthread.php?t=198107&highlight=jdk)

incubus

---

### Post by JeremyWorst on 2006-06-22
Thanks for your response, incubus, but I think I should take care of something else first.  I've been getting all updates from Update Manager, but just today got the offer to upgrade to Ubuntu 6.06.  I thought I'd already done that.  Let me do the upgrade today, then probably the advice in this thread will work for me.

---

