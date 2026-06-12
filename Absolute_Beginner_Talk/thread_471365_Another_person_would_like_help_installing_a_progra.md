---
title: "Another person would like help installing a program"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ipreferpi on 2007-06-11
Like many other people, I am have no experience installing apps and tutorials don't seem to help. 
[http://img353.imageshack.us/img353/8314/screenshotjin2141filebrah2.png](http://img353.imageshack.us/img353/8314/screenshotjin2141filebrah2.png)
Here is a screen shot of a folder with the application. What should I do? thanks for your help.

---

### Post by brownknight on 2007-06-11
just doubleclick on the "jin" file. hope this helps.

---

### Post by taurus on 2007-06-11
Looks to me like it's a java stuff.  You just run it from a terminal like

```
java jin.jar
-or-
./jin
```
Otherwise, read README on how to run or install it.

```
less README
```

And of course, you need to have either Sun or Blackdown java installed on your machine first.

```
java -version
```

---

### Post by ipreferpi on 2007-06-11
i have tried clicking on the jin file and a box pops up with run as an option, but nothing happens after that.

java -version returns 
"jonathan@jonathan-laptop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)"

when i try installing with the terminal it returns:
You seem to be running GNU's Java implementation, which is incomplete.
Jin requires Sun's Java (or a fully compatible version) 1.4 or later.
If you can't install it with your distribution's package manager, you
can obtain and install it manually from [http://www.java.com](http://www.java.com)

if i try to run the jin.jar it returns:

jonathan@jonathan-laptop:~/jin-2.14.1$ java -jar jin.jar
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.Font.tk(libgcj.so.70)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.70)
   at java.awt.Font.<init>(libgcj.so.70)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.70)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.70)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.70)
   at javax.swing.UIManager.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at free.jin.Jin.restoreLookAndFeel(Unknown Source)
   at free.jin.Jin.<init>(Unknown Source)
   at free.jin.Jin.createInstance(Unknown Source)
   at free.jin.JinApplication.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...15 more
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities.getOwnerFrame(libgcj.so.70)
   at javax.swing.JOptionPane.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at free.jin.JinApplication.main(Unknown Source)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...9 more


I think there is something wrong with how i installed java, though i used the add/remove applications program and the synaptic manager.

---

### Post by taurus on 2007-06-11
You have a wrong version of java on your machine.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```
Now, run your program again.

---

### Post by ipreferpi on 2007-06-11
still nothing. I assume I don't need to restart.

---

### Post by pppetter on 2007-06-11
Does "java -version" give you something like this then
> java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

?

---

### Post by ipreferpi on 2007-06-12
jonathan@jonathan-laptop:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

It doesn't look like that step changed anything. 

java -version still gives the same thing:
jonathan@jonathan-laptop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


edit: i got it to upgrade to 1.6, but the program still doesn't work on the website or here.

---

