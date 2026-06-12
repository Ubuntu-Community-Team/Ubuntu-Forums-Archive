---
title: "programming in java"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-21
Hi, I was interested in relearning my college java.  Problem is, now that I have installed  ubuntu, I don't know what I need to compile java source code.  Is vim a good editor to write in java?  If so how would I get access to vim.  I am very new to ubuntu as well as linux so i don't know many commands.

---

### Post by DJ_Max on 2005-08-21
Before you start developing on a system you don't know much about, you want to read as much as possible, and use Google.
[http://tldp.org/](http://tldp.org/)
[http://linuxcommand.org/](http://linuxcommand.org/)
[https://wiki.ubuntu.com/Java](https://wiki.ubuntu.com/Java)

Look at [Eclipse](https://wiki.ubuntu.com/EclipseIDE) for an IDE. Or take a look at emacs.

---

### Post by RastaMahata on 2005-08-21
its kinda easy...
first, enable backports-extra: [How to enable extra repositories](http://www.ubuntuguide.org/#extrarepositories)
After you enable the repos, install java from synaptic. The package is sun-j2sdk1.5
Then, to write a java class, vim si good, but gedit does the job well too. Applications > Accesories > Text editor.
Just save the .java file to your home folder (or create a java folder inside your home folder), and then go to a console, and type javac <name>.java
You'll have a <name>.class file that you can run with java <name>

Here's a helo world java source code:```
class HelloWorld {
public static void main (String args[]) {
System.out.println("Hello World");
}
}
```
You should save it as the class name. In this case, HelloWorld.java

Good luck.

---

