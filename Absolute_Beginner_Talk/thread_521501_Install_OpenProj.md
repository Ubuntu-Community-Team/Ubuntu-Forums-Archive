---
title: "Install OpenProj"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by dpatel on 2007-08-09
I am trying to install OpenProj on Ubuntu 7.04. I've downloaded it and done what it says in the readme:
> 
Running OpenProj beta 2

Requirements:
	OpenProj uses the Java Runtime Environment version 1.5 or later.  1.6 is preferred.
	To see what version you have, check out this page:
	[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

	You can download java here:  [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)

Installation:
	Unzip the files to the folder of your choice.
	
	Linux: Open a terminal, go to the openproj_beta2 folder and run ./openproj.sh (assuming you downloaded the tar.gz archive).	If you get a permission denied message, do "chmod +x openproj.sh"  This will let you run the shell script. You can also run with the command "sh openproj.sh"
				
We will soon be releasing a windows installer as well as packages for Linux.	

But when I run the openproj.sh script, I get the following:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
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
   at com.projity.pm.graphic.gantt.Main.main(Main.java:37)
   at com.projity.main.Main.main(Main.java:27)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...13 more
```

I've got Java RE6 on my machine (I did sudo apt-get install sun-java6-jre and it says I've already got the latest version).

Any ideas where I'm going wrong?

---

### Post by Elegorod on 2007-08-12
Sun java 6 has been installed, but it is not used. Try open terminal and execute command:
```

sudo update-alternatives --config java

```
Choose alternative that corresponds to sun java 6.

---

