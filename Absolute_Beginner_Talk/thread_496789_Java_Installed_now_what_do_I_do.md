---
title: "Java Installed: now what do I do?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Tsu Dho Nimh on 2007-07-09
Ubuntu 7.04 64-bit
AMD processor
2G RAM

Ubuntu shows that various kinds of Java are installed:

Sun Java 5.0 Runtime
Sun Java 6 Web Start (32 bit)
Java Web Start 1.4 (blackdown)
Java 1.4 plugin foir mozilla


Now, how do I get java applications to run?  I download them, let the installer do its work, and the jars and such show up in a directory. 

Then WHAT? That part is glossed over, as if something is going to magically happen.

---

### Post by Inxsible on 2007-07-09
> **Tsu Dho Nimh said:**
> Ubuntu 7.04 64-bit
AMD processor
2G RAM

Ubuntu shows that various kinds of Java are installed:

Sun Java 5.0 Runtime
Sun Java 6 Web Start (32 bit)
Java Web Start 1.4 (blackdown)
Java 1.4 plugin foir mozilla


Now, how do I get java applications to run?  I download them, let the installer do its work, and the jars and such show up in a directory. 

Then WHAT? That part is glossed over, as if something is going to magically happen.
What do you want to do with Java ? 
Most likely, you do not develop Java code, so what you have installed will help you in browsing to websites that use Java. it will also help you start Java applets, which are hosted by someone on their websites (Java WebStart is used for this).

The runtime environment just ensures that you can execute Java programs. So next time you visit any Java enabled websites, they should run without a hitch...provided everything was installed correctly and without errors.

---

### Post by steve.horsley on 2007-07-09
To launch a jar file, the comand is:
**java -jar whateverItsCalled.jar**
but I believe that most installers will create a script that you can execute directly, which then launches the java interpreter.

---

### Post by Tsu Dho Nimh on 2007-07-09
> **steve.horsley said:**
> To launch a jar file, the comand is:
**java -jar whateverItsCalled.jar**
but I believe that most installers will create a script that you can execute directly, which then launches the java interpreter.

Thanks ... it has a script, but it doesn't seem to be working. Neither does the direct command you gave. 

It works with Windows 2000, which makes it even more annoying.

---

### Post by steve.horsley on 2007-07-10
"doesn't work" is rather vague. What's the error message?

---

